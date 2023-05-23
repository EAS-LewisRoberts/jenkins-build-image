pipeline {
    agent any
    
    stages {
        stage('Clone Repository') {
            steps {
                // Clone the Git repository
                git 'https://github.com/your-git-repo.git'
            }
        }
        
       stage('Build Docker Image') {
            steps {
                // Build the Docker image
                script {
                    docker.withRegistry('https://hub.docker.com/repositories/lewisroberts', 'fbd6ebb3-ae93-48c3-8116-88eeac06b1c7') {
                        def imageName = 'LewisRoberts/frontend'
                        def imageTag = 'latest'
                        
                        docker.build(imageName + ':' + imageTag, '.').push()
                    }
                }
            }
        }

        stage('Tag') {
            steps {
                sh 'docker tag frontend lewisroberts/frontend:latest'
            }
        }

        stage('Push') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'fbd6ebb3-ae93-48c3-8116-88eeac06b1c7', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
                    sh 'docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD'
                    sh 'docker push LewisRoberts/frontend:latest'
                }
            }
        }
    }
}


