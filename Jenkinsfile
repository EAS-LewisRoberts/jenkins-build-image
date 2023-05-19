pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
    }
    stages {
        stage ('Test') {
            steps {
                echo 'testing the application...'
            }
        }
        stage ('Build') {
            steps { 
                echo 'building the application...'
            }
        }
        stage ('deploy') {
            steps {
                echo 'depolying the application...'
            }
        }
    }
}
