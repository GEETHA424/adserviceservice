pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout your code from a Git repository
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Build your application (e.g., with Maven, Gradle, etc.)
                echo "geetha"
            }
        }

        stage('Test') {
            steps {
                // Run your tests here (e.g., unit tests, integration tests)
                echo "hi peddinni"
            }
        }

        stage('Build image') {
            steps {
                script {
                    // Build the Docker image
                    dockerImage = docker.build("geethapeddinni/jenkins-docker:latest", '.')
                }
            }
        }

        stage('Push image') {
            steps {
                script {
                    // Push the Docker image to a registry
                    withDockerRegistry([credentialsId: 'dckr_pat_wi7oCqwdSPG51qjEWTZPNVB2lUw', url: 'https://index.docker.io/v1/']) {
                        dockerImage.push()
                    }
                }
            }
        }
    }

    post {
        success {
            // Perform actions when the pipeline succeeds (e.g., notifications)
            echo 'Pipeline succeeded!'
        }
        failure {
            // Perform actions when the pipeline fails (e.g., notifications)
            echo 'Pipeline failed!'
        }
    }
}
