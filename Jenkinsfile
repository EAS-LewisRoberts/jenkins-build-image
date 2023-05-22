pipeline{
    
  agent any
    
  stages {
         stage('Clone repository') {
           steps {
             git credentialsId: 'git', url: 'https://github.com/EAS-LewisRoberts/jenkins-build-image'
           }
         }
    
         stage('Build image') {
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
    
node {   
    //script
}
