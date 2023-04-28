pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('romashka123-dockerhub')
    }
    stages {
        stage('Docker version') {
            steps {
                sh '''
                    echo $USER
                    docker version
                '''
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t romaashka123/html:latest .'
            }
        }
        stage('Login') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push'){
            steps{
                sh 'docker push romashka123/html:latest'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}
  
