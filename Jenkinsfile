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
            sh 'cd vote && sudo docker build -t 341888801287.dkr.ecr.us-east-1.amazonaws.com/vote:${BUILD_NUMBER} .'
            sh 'sudo docker push 341888801287.dkr.ecr.us-east-1.amazonaws.com/vote:${BUILD_NUMBER}'
          }
        }
      }
    }
  }
} 
