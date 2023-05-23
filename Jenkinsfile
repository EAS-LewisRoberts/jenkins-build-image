pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t frontend .'
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


