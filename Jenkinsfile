pipeline {
  agent {
    label 'worker'
  }
  stages {
    stage('Git Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build Docker Image') {
      parallel {
        stage('Build Docker Image') {
          steps {
            sh 'cd vote && docker build -t 341888801287.dkr.ecr.us-east-1.amazonaws.com/vote:${BUILD_NUMBER} .'
            sh 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 341888801287.dkr.ecr.us-east-1.amazonaws.com'
            sh 'docker push 341888801287.dkr.ecr.us-east-1.amazonaws.com/vote:${BUILD_NUMBER}'
          }
        }
      }
    }
  }
} 
