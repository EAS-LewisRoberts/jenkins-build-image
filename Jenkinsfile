pipeline {
    agent any

      stages {
          stage('Build Frontend Image') {
              steps {
                  script {
                      docker.withRegistry('https://hub.docker.com/repositories/lewisroberts', 'dockerhub-credentials') {
                          def frontendImage = docker.build('EAS-LewisRoberts/frontend-image:${env.BUILD_NUMBER}', './frontend')
                          frontendImage.push()
                      }
                  }
              }
          }

          stage('Build Backend Image') {
              steps {
                  script {
                      docker.withRegistry('https://hub.docker.com/repositories/lewisroberts', 'dockerhub-credentials') {
                          def backendImage = docker.build('EAS-LewisRoberts/backend-image:${env.BUILD_NUMBER}', './backend')
                          backendImage.push()
                      }
                  }
              }
          }
      }
}
