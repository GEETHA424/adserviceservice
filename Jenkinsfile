pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t geetha.peddinni/jenkins-docker-hub .'
      }
    }
    stage('Login') {
      steps {
        script {
          // Use Docker Hub credentials from environment
          withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable: 'DOCKERHUB_CREDENTIALS_PSW', usernameVariable: 'DOCKERHUB_CREDENTIALS_USR')]) {
            sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
          }
        }
      }
    }
    stage('Push') {
      steps {
        sh 'docker push geetha.peddinni/jenkins-docker-hub'
      }
    }
  }
  post {
    always {
      // Remove or correct the following step based on your requirements
      sh 'echo "This is a placeholder for post-processing"'
    }
  }
}
