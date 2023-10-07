pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '5'))
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('docker-hub')
        DOCKER = "${dockerTool}/bin"
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    def dockerImage = docker.build('geethapeddinni/jenkins-docker-hub:latest', '.')
                }
            }
        }
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push geethapeddinni/jenkins-docker-hub'
            }
        }
        stage('Syft Scan') {
            steps {
                // Run Syft to analyze the Docker image
                sh 'syft --json geethapeddinni/jenkins-docker-hub'
            }
        }
    }
    post {
        always {
            sh 'docker logout'
        }
    }
}
