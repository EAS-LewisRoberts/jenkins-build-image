pipeline {
   agent any 
   environment {
      NEW_VERSION = '1.3.0'
      SERVER_CREDENTIALS = credentials('server-credentials')
   }
    
    stages {
         stage("build") {
            when {
               expression {
                  BRANCH_NAME == 'dev' && CODE_CHANGES == true
               }
            }
          steps {
            echo 'building the application..'
             sh "ls -a"
             dockerimage = docker.build("lewisroberts/backend:latest")
          }
         }
    
         stage('Clone repository') {
           steps {
             git credentialsId: 'git', url: 'https://github.com/EAS-LewisRoberts/jenkins-build-image'
           }
         }

         stage("test") {
            when {
               expression {
                  BRANCH_NAME == 'dev' || BRANCH_NAME == 'main'
          steps {
            echo 'testing the application..'
          }
         }
         stage("deploy") {
          steps {
            echo 'deploying the application..'
          }
         }
    }
}
