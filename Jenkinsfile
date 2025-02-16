pipeline {
  agent any
  stages {
    stage('casestudy-calculation') {
      parallel {
        stage('casestudy-calculation') {
          steps {
            dir(path: 'source/calculation-offer-service/CalculationServiceAPISolution') {
              sh 'pwd'
              sh 'docker build -t $CALCULATION_SERVICE_IMAGE:latest -t $CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER .'
              sh 'docker tag $CALCULATION_SERVICE_IMAGE:latest $ECR_ID/$CALCULATION_SERVICE_IMAGE:latest'
              sh 'docker tag $CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER $ECR_ID/$CALCULATION_SERVICE_IMAGE:$BUILD_NUMBER'
              sh 'docker login --username $ECR_CREDENTIALS_USR --password $ECR_CREDENTIALS_PSW $ECR_ID'
              sh 'docker image prune -f'
              sh 'docker push $ECR_ID/$CALCULATION_SERVICE_IMAGE:latest'
            }

          }
        }

        stage('creditcard-identity-verification-response-daemon') {
          steps {
            dir(path: 'source/creditcard-identity-verification-response-daemon') {
              sh 'pwd'
              sh 'docker build -t $CREDITCARD_RESPONSE_DAEMON:latest -t $CREDITCARD_RESPONSE_DAEMON:$BUILD_NUMBER .'
              sh 'docker tag $CREDITCARD_RESPONSE_DAEMON:latest $ECR_ID/$CREDITCARD_RESPONSE_DAEMON:latest'
              sh 'docker tag $CREDITCARD_RESPONSE_DAEMON:$BUILD_NUMBER $ECR_ID/$CREDITCARD_RESPONSE_DAEMON:$BUILD_NUMBER'
              sh 'docker image prune -f'
              sh 'docker push $ECR_ID/$CREDITCARD_RESPONSE_DAEMON:latest'
            }

          }
        }

        stage('creditcard-service') {
          steps {
            dir(path: 'source/creditcard-service') {
              sh 'pwd'
              sh 'docker build -t $CREDIT_SERVICE:latest -t $CREDIT_SERVICE:$BUILD_NUMBER .'
              sh 'docker tag $CREDIT_SERVICE:latest $ECR_ID/$CREDIT_SERVICE:latest'
              sh 'docker tag $CREDIT_SERVICE:$BUILD_NUMBER $ECR_ID/$CREDIT_SERVICE:$BUILD_NUMBER'
              sh 'docker image prune -f'
              sh 'docker push $ECR_ID/$CREDIT_SERVICE:latest'
            }

          }
        }

        stage('email-service') {
          steps {
            dir(path: 'source/email-service') {
              sh 'pwd'
              sh 'docker build -t $EMAIL_SERVICE:latest -t $EMAIL_SERVICE:$BUILD_NUMBER .'
              sh 'docker tag $EMAIL_SERVICE:latest $ECR_ID/$EMAIL_SERVICE:latest'
              sh 'docker tag $EMAIL_SERVICE:$BUILD_NUMBER $ECR_ID/$EMAIL_SERVICE:$BUILD_NUMBER'
              sh 'docker image prune -f'
              sh 'docker push $ECR_ID/$EMAIL_SERVICE:latest '
            }

          }
        }

        stage('identity-verification-service') {
          steps {
            dir(path: 'source/identity-verification-service') {
              sh 'pwd'
              sh 'docker build -t $IDENTITY_VERIFICATION:latest -t $IDENTITY_VERIFICATION:$BUILD_NUMBER .'
              sh 'docker tag $IDENTITY_VERIFICATION:latest $ECR_ID/$IDENTITY_VERIFICATION:latest'
              sh 'docker tag $IDENTITY_VERIFICATION:$BUILD_NUMBER $ECR_ID/$IDENTITY_VERIFICATION:$BUILD_NUMBER'
              sh 'docker image prune -f'
              sh 'docker push $ECR_ID/$IDENTITY_VERIFICATION:latest'
            }

          }
        }

      }
    }

  }
  environment {
    ECR_ID = '142198642907.dkr.ecr.ca-central-1.amazonaws.com'
    CALCULATION_SERVICE_IMAGE = 'tejasv2-casestudy-calculation-service'
    ECR_CREDENTIALS = credentials('ecr-credentials')
    CREDITCARD_RESPONSE_DAEMON = 'tejasv2-creditcard-identity-verification-response-daemon'
    CREDIT_SERVICE = 'tejasv2-creditcard-service'
    EMAIL_SERVICE = 'tejasv2-email-service'
    IDENTITY_VERIFICATION = 'tejasv2-identity-verification-service'
  }
}