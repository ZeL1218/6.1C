pipeline {
    agent any

    options {
        logRotator(numToKeepStr: '1')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Build the code using a build automation tool.'
                echo 'Tool: Maven (or another build tool like Gradle, Ant)'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Run unit tests to ensure code functions as expected and integration tests to ensure components work together.'
                echo 'Tool: JUnit (for unit tests), TestNG (for integration tests)'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Perform code analysis to ensure it meets industry standards.'
                echo 'Tool: SonarQube (for code quality analysis)'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Perform a security scan to identify vulnerabilities in the code.'
                echo 'Tool: OWASP Dependency-Check (for security vulnerabilities)'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploy the application to a staging server.'
                echo 'Tool: AWS CLI (for deployment to AWS EC2 or S3)'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Run integration tests on the staging environment to ensure the application works in a production-like setting.'
                echo 'Tool: Selenium (for integration testing)'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploy the application to a production server.'
                echo 'Tool: AWS CLI (for deployment to AWS EC2 or S3)'
            }
        }
    }

    post {
        always {
            emailext attachLog: true, 
                     to: 's223926313@deakin.edu.au',
                     subject: "Pipeline completed",
                     body: "Please find the log attached."
        }
    }
}
