pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven 3.23'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests with JUnit...'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing the code with SonarQube...' 
                
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan with OWASP Dependency Check...'
                sh 'mvn org.owasp:dependency-check-maven:check'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
            }
        }
    }

    post {
        success {
            mail to: 's223926313@deakin.edu.au',
                subject: "Pipeline succeeded",
                body: "The pipeline has completed successfully."
        }
        failure {
            mail to: 's223926313@deakin.edu.au',
                subject: "Pipeline failed",
                body: "The pipeline has failed. Please check the logs."
        }
    }
}
