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
        echo "hi geetha peddinni"
            }
        }

        stage('Test') {
            steps {
                // Run your tests here (e.g., unit tests, integration tests)
                //sh './run_tests.sh'
                echo " hi peddinni"
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
