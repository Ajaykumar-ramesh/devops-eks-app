pipeline {
  agent any

  environment {
    AWS_REGION = "ap-south-1"
    ECR_REPO   = "460425809337.dkr.ecr.ap-south-1.amazonaws.com/devops-app-repo"
    IMAGE_TAG  = "${BUILD_NUMBER}"
  }

  stages {

    stage('Checkout') {
      steps {
        git branch: 'main',
            url: 'https://github.com/zororoman/devops-eks-app.git'
      }
    }

    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv('sonarqube') {
          sh '''
            sonar-scanner \
              -Dsonar.projectKey=devops-eks-app \
              -Dsonar.sources=.
          '''
        }
      }
    }

    stage('Quality Gate') {
      steps {
        timeout(time: 1, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
      }
    }

    stage('Trivy FS Scan') {
      steps {
        sh 'trivy fs --exit-code 0 --severity HIGH,CRITICAL .'
      }
    }

    stage('Docker Build') {
      steps {
        sh 'docker build -t devops-app:${IMAGE_TAG} .'
      }
    }

    stage('Trivy Image Scan') {
      steps {
        sh 'trivy image --exit-code 0 --severity HIGH,CRITICAL devops-app:${IMAGE_TAG}'
      }
    }

    stage('Push to ECR') {
      steps {
        withCredentials([[
          $class: 'AmazonWebServicesCredentialsBinding',
          credentialsId: 'aws-creds'
        ]]) {
          sh '''
            aws ecr get-login-password --region ${AWS_REGION} \
              | docker login --username AWS --password-stdin ${ECR_REPO}

            docker tag devops-app:${IMAGE_TAG} ${ECR_REPO}:${IMAGE_TAG}
            docker push ${ECR_REPO}:${IMAGE_TAG}
          '''
        }
      }
    }
  }
}
