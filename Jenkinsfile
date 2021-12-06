pipeline {
  agent any
  stages {
    stage('docker-cmds') {
      steps {
        sh 'pwd'
      }
    }

  }
  environment {
    ECR_ID = '142198642907.dkr.ecr.ca-central-1.amazonaws.com'
    CALCULATION_SERVICE_IMAGE = 'tejasv2-casestudy-calculation-service'
  }
}