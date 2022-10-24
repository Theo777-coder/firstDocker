pipeline {
    agent any
    environment {
		DOCKERHUB_CREDENTIALS=credentials('DockerHub')
	}
    stages {
        stage('Build') {
            steps {
                sh "sudo docker build -t theo777c270/simple_server ."
            }
        }
        stage('Run') {
            steps {
                sh 'sudo service docker stop'
                sh 'sudo service docker start'
                sh "sudo docker run -d -p 8000:5000 theo777c270/simple_server"
            }
        }
        stage('Push to Dockerhub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | sudo docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'sudo docker push theo777c270/simple_server'
            }
        }
    }
}