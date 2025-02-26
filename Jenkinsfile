pipeline {
    agent any
    environment {
		DOCKERHUB_CREDENTIALS = credentials('docker')
	}
    stages {
        stage('Login') {

			steps {
               sh 'echo $DOCKERHUB_CREDENTIALS_USR'
              sh 'echo $DOCKERHUB_CREDENTIALS_PSW'
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR -p  $DOCKERHUB_CREDENTIALS_PSW' 
			}
		}
        stage('Build Image') {
            steps {
              sh 'docker build -t moredatta574/flask_jenkins .'
            }
        }
        stage('Run Image') {
            steps {
               sh 'docker run -d  -p 9090:9191 --name flask_container moredatta574/flaskjenkins'
            }
        }
        
        stage('Test') {
            steps {
                'echo 'Successfully Pushed'
            }
        }
    }
}
