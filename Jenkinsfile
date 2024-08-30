pipeline {
    agent any
    
    tools {
        maven 'Maven 3.x' // 引用你在Jenkins中配置的Maven名称
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the code using Maven...'
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests with JUnit...'
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Analyzing the code with SonarQube...'
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
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
                sh './deploy.sh staging'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
                sh './run_integration_tests.sh staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                sh './deploy.sh production'
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
