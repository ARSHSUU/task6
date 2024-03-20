pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Performing build using Maven...'
            }
        }
        
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests...'
                echo 'Running integration tests...'
            }
        }
        
        stage('Code Quality Check') {
            steps {
                echo 'Analyzing code quality with SonarQube...'
            }
        }
        
        stage('Security Assessment') {
            steps {
                echo 'Conducting security assessment using OWASP ZAP...'
            }
        }
        
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging server (e.g., AWS EC2 instance)...'
            }
        }
        
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging environment...'
            }
        }
        
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production server (e.g., AWS EC2 instance)...'
            }
        }
    }
    post {
        success {
            emailext subject: "Pipeline Success: '${currentBuild.fullDisplayName}'",
                      body: 'The pipeline completed successfully.',
                      to: 'arsh4765.be22@chitkara.edu.in',
                      attachLog: true
        }
        failure {
            emailext subject: "Pipeline Failure: '${currentBuild.fullDisplayName}'",
                      body: 'The pipeline encountered a failure. Please investigate.',
                      to: 'arsh4765.be22@chitkara.edu.in',
                      attachLog: true
        }
    }
}

