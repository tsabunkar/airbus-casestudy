pipeline {
  agent any
  stages {
    stage('docker-cmds') {
      steps {
        dir(path: 'source/calculation-offer-service/CalculationServiceAPISolution') {
          sh 'pwd'
        }

        sh 'docker build -t $CALCULATION_SERVICE_IMAGE:latest -t $CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER .'
      }
    }

  }
  environment {
    ECR_ID = '142198642907.dkr.ecr.ca-central-1.amazonaws.com'
    CALCULATION_SERVICE_IMAGE = 'tejasv2-casestudy-calculation-service'
  }
}