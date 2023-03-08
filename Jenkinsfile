pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('docker-cred-franc')
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t fdjapi10/nodeapp:latest .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push fdjapi10/nodeapp:latest'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
