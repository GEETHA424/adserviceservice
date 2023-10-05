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
                sh './build.sh'
            }
        }

        stage('Test') {
            steps {
                // Run your tests here (e.g., unit tests, integration tests)
                sh './run_tests.sh'
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Deploy your application to a staging environment
                sh './deploy_to_staging.sh'
            }
        }

        stage('Promote to Production') {
            when {
                // Define conditions for promoting to production (e.g., manual approval)
                expression { currentBuild.resultIsBetterOrEqualTo('SUCCESS') }
            }
            steps {
                // Deploy your application to production
                sh './deploy_to_production.sh'
            }
        }
    }

    post {
        success {
            // Perform actions when the

