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
          }
         }
         stage("test") {
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
