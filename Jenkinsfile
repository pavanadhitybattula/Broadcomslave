pipeline{
	agent any
	environment {
		DOCKERHUB_CREDENTIALS=credentials('adityadockerhub')
	}

	stages {
		stage('Build') {
			steps {
				sh 'docker build -t pavanaditya103/jenkinsbuild103:latest .'
			}
		}
		stage('Login') {
			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}
		stage('Push') {
			steps {
				sh 'docker push pavanaditya103/jenkinsbuild103:latest'
			}
		}
	}
	post {
		always {
			sh 'docker logout'
		}
	}
}
