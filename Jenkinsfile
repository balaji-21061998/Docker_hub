pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('Docker_hub')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh ' docker build -t tomcat:v4 .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push image') {
            steps{
                sh ' docker push balajipedada/balaji-techie:v4'
            }
        }
}

}
