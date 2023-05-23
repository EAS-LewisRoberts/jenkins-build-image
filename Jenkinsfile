pipeline {
    agent any

    stages {
        stage('Fetch Code') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build Frontend Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-credentials') {
                        def frontendImage = docker.build('your-username/frontend-image:${env.BUILD_NUMBER}', './frontend')
                        frontendImage.push()
                    }
                }
            }
        }

        stage('Build Backend Image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub-credentials') {
                        def backendImage = docker.build('your-username/backend-image:${env.BUILD_NUMBER}', './backend')
                        backendImage.push()
                    }
                }
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
