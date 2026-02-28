pipeline {
    agent any

    environment {
        ACR_NAME = "praveenacrdocker"
        IMAGE_NAME = "flaskapp"
        ACR_LOGIN = "praveenacrdocker.azurecr.io"
    }

    stages {

        stage('Checkout') {
            steps {
                git 'git 'https://github.com/praveenkreddy56-source/azure-devops-app.git''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME:v1 .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag $IMAGE_NAME:v1 $ACR_LOGIN/$IMAGE_NAME:v1'
            }
        }

        stage('Push to ACR') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'acr-creds',
                usernameVariable: 'USERNAME',
                passwordVariable: 'PASSWORD')]) {
                    sh 'echo $PASSWORD | docker login $ACR_LOGIN -u $USERNAME --password-stdin'
                    sh 'docker push $ACR_LOGIN/$IMAGE_NAME:v1'
                }
            }
        }
    }
}
