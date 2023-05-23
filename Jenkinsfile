pipeline {
  agent any

  environment {
    registryCredential = 'dockerhub'
  }

  stages {
    stage('Build') {
      steps {
        git 'https://github.com/EAS-LewisRoberts/jenkins-build-image.git'
        sh 'docker build -t LewisRoberts/frontend.'
      }
    }
     
    stage('Login') {
      steps {
        withCredentials([
          usernamePassword(
            credentialsId: 'dockerhub',
            usernameVariable: 'DOCKER_USER',
            passwordVariable: 'DOCKER_PASSWORD'
          )
        ]) {
          sh "docker login -u $DOCKER_USER -p $DOCKER_PASSWORD"
        }
      }
    }

    stage('Push') {
      steps {
        sh 'docker push EAS-LewisRoberts/frontend'
      }
    }
      
  }
}


