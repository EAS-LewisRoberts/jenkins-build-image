pipeline {
    agent any
    environment {
        NEW_VERSION = '1.3.0'
    }
    stages {
        stage ('Build') {
            steps { 
                echo 'building the application...'
            }
        }
        stage ('Test') {
            steps {
                echo 'testing the application...'
            }
        }
        stage ('deploy') {
            steps {
                echo 'depolying the application...'
            }
        }
    }
}
