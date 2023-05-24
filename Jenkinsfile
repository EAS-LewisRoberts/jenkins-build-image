pipeline {
  // The agent any directive indicates that the pipeline can be run on any available agent.
  agent any
  //The environment block defines an environment variable named registryCredential and sets it to 'dockerhub'. This variable is used later in the script.
  environment {
    registryCredential = 'dockerhub'
  }
//The stages block contains the different stages of the pipeline. a. The first stage is named "Build". Within this stage, the Git repository at https://github.com/EAS-LewisRoberts/jenkins-build-image.git is cloned using the git step. After that, the docker build command is executed to build a Docker image named jenkins-build-image/frontend. The -t option is used to tag the image with the given name. Please note that there seems to be a period (.) at the end of the docker build command, which might be a typo. It should be removed, and the command should look like this: sh 'docker build -t jenkins-build-image/frontend'.
  stages {
    stage('Build') {
      steps {
        sh 'ls ./frontend'
        sh 'docker build -t jenkins-build-image/frontend ./frontend'
      }
    }
     //The second stage is named "Login". Within this stage, the Docker Hub credentials are obtained using the withCredentials block and the usernamePassword method. The credentials are identified by the credentialsId parameter, which is set to 'dockerhub'. The username and password are stored in the DOCKER_USER and DOCKER_PASSWORD variables, respectively. The sh step is then used to execute the docker login command, passing the values of the DOCKER_USER and DOCKER_PASSWORD variables as arguments.
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
    //The third stage is named "Push". Within this stage, the docker push command is executed to push the previously built image, jenkins-build-image/frontend, to Docker Hub.
    stage('Push') {
      steps {
        sh 'docker push jenkins-build-image/frontend'
      }
    }
      
  }
}


