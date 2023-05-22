pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-lewisroberts')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t lewsiroberts/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-root'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push lewisroberts/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
