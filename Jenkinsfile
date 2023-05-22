pipeline{
    
  agent any
    
  stages {
      stage('test') {
          when {
              expression {
                  BRANCH_NAME == 'dev' || BRANCH_NAME == 'master'
              }
          }
          steps {
              echo 'testing the application...'
      }
         stage('Clone repository') {
           steps {
             git credentialsId: 'git', url: 'https://github.com/EAS-LewisRoberts/jenkins-build-image'
           }
         }
    
         stage('Build image') {
             when {
                 expression {
                     BRANCH_NAME =='dev' && CODE_CHANGES == true
                 }
             }
           steps {
             dockerImage = docker.build("lewisroberts/image1:latest")
           }
         }
    
         stage('Push image') {
           steps {
             withDockerRegistry([ credentialsId: "dockerhubaccount", url: "https://hub.docker.com/repositories/lewisroberts" ]) {
                      dockerImage.push()
             }
           }
         }
   }   
  }
}
