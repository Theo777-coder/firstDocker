pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh "sudo docker build -t py_server ."
            }
        }
        stage('Run') {
            steps {
                sh 'sudo service docker stop'
                sh 'sudo service docker start'
                sh "sudo docker run -d -p 7777:5000 py_server"
            }
        }
        stage('Push to Dockerhub') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
                sh 'docker push theo777c270/pyserver:latest'
            }
        }
    }
}
