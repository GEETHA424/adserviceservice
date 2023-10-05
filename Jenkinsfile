pipeline {
  agent any
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dckr_pat_wi7oCqwdSPG51qjEWTZPNVB2lUw') // Use the credential ID you created in step 2
  }
  stages {
    stage('Build and Push Docker Image') {
      steps {
        script {
          // Build the Docker image
          sh 'docker build -t jenkins-hub:tag .'

          // Authenticate with Docker Hub
          withCredentials([usernamePassword(credentialsId: 'dckr_pat_wi7oCqwdSPG51qjEWTZPNVB2lUw', passwordVariable: 'DOCKERHUB_PASSWORD', usernameVariable: 'DOCKERHUB_USERNAME')]) {
            sh 'echo $DOCKERHUB_PASSWORD | docker login -u $DOCKERHUB_USERNAME --password-stdin'
          }

          // Push the Docker image to Docker Hub
          sh 'docker push jenkins-hub:latest'
        }
      }
    }
  }
}

