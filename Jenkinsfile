pipeline {
    agent any
    environment {
        DOCKERHUB_CREDENTIALS = credentials('romaxa09-dockerhub')
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
                sh 'docker build -t roman/html:latest .'
            }
        }
        stage('Login') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push'){
            steps{
                sh 'docker push roman/html:latest'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}
  
