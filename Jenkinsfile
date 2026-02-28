pipeline {
    agent any

    environment {
        ACR_NAME = "praveenacrdocker"
        IMAGE_NAME = "flaskapp"
        ACR_LOGIN = "praveenacrdocker.azurecr.io"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:v1 .'
            }
        }
}
