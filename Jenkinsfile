pipeline{
    node {   
         stage('Clone repository') {
             git credentialsId: 'git', url: 'https://github.com/EAS-LewisRoberts/jenkins-build-image'
         }
    
         stage('Build image') {
             dockerImage = docker.build("lewisroberts/image1:latest")
         }
    
         stage('Push image') {
             withDockerRegistry([ credentialsId: "dockerhubaccount", url: "" ]) {
                      dockerImage.push()
         }
       }    
    }
}
