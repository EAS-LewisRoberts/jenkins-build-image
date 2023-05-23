pipeline {
    agent any
    
    stages {
        stage('Build Image') {
            steps {
                script {
                    def imageName = 'lewisroberts/frontend'
                    def imageTag = 'latest'
                    
                    // Build Docker image
                    docker.build(imageName + ':' + imageTag)
                }
            }
        }
        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'lewisroberts', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
                    // Login to Docker Hub
                    sh 'docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD'
                    
                    // Push the image to Docker Hub
                    sh "docker push ${frontend}:${frontend}"
                }
            }
        }
    }
}

