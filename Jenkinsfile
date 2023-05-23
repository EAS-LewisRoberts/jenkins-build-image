pipeline {
    agent any
    
    stages { 
       stage('Build Docker Image') {
            steps {
                // Builds the Docker image
                script {
                    docker.withRegistry('https://hub.docker.com/repositories/lewisroberts', 'fbd6ebb3-ae93-48c3-8116-88eeac06b1c7') {
                        def imageName = 'LewisRoberts/frontend'
                        def imageTag = 'latest'
                        
                        docker.build(imageName + ':' + imageTag, '.').push()
                    }
                }
            }
        }

        stage('Login to Docker Hub') {
            steps {
                withCredentials([
                    usernamePassword(credentialsId: 'fbd6ebb3-ae93-48c3-8116-88eeac06b1c7', usernameVariable: 'DOCKERHUB_USERNAME', passwordVariable: 'DOCKERHUB_PASSWORD')
                ]) {
                    script {
                        def dockerHubRegistry = 'https://hub.docker.com/repositories/lewisroberts'
                        def dockerImage = 'lewisroberts/frontend'
                        def dockerTag = 'latest'
                        
                        docker.withRegistry(dockerHubRegistry, 'docker') {
                            // Login to Docker Hub
                            docker.login(username: DOCKERHUB_USERNAME, password: DOCKERHUB_PASSWORD)
                            
                            // Build and push the Docker image
                            docker.image(dockerImage).tag("${lewisroberts}:${frontend}").push()
                        }
                    }
                }
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


