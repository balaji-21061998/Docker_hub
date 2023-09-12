pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh ' docker build -t balajipedada/tomcat:v6 .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh ' docker push balajipedada/tomcat:v6'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
