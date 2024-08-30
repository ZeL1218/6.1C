pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
                sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                sh 'snyk test'
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                sh 'scp target/myapp.jar ec2-user@your-ec2-instance:/path/to/deploy'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                sh 'curl http://your-staging-url/api/test'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                sh 'scp target/myapp.jar ec2-user@your-prod-instance:/path/to/deploy'
            }
        }
    }

    post {
        always {
            echo 'This will always run after the stages finish'
        }
        success {
            echo 'This will run only if all stages pass'
        }
        failure {
            echo 'This will run if any stage fails'
        }
    }
}
