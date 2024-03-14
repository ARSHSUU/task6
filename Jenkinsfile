pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Installing dependencies...'
                echo 'Building application...'
                git branch: 'main', url: 'https://github.com/yourusername/yourrepository'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                
                script {
                    def powershellScript = """
                        \$MailServer = "smtp.example.com"
                        \$MailFrom = "sender@example.com"
                        \$MailTo = "recipient@example.com"
                        \$MailSubject = "Test Results"
                        \$MailBody = "Tests executed successfully."
                        \$MailUsername = "yourusername"
                        \$MailPassword = ""
    
                        Send-MailMessage -From \$MailFrom -To \$MailTo -Subject \$MailSubject -Body \$MailBody -SmtpServer \$MailServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential \$MailUsername, (ConvertTo-SecureString -AsPlainText \$MailPassword -Force))
                    """
                    powershell(powershellScript)
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis...'
            }
        }
        stage('Security') {
            steps {
                echo 'Running security checks...'
                
                script {
                    def powershellScript = """
                        \$MailServer = "smtp.example.com"
                        \$MailFrom = "sender@example.com"
                        \$MailTo = "recipient@example.com"
                        \$MailSubject = "Security Check Results"
                        \$MailBody = "Security scans passed."
                        \$MailUsername = "yourusername"
                        \$MailPassword = ""
    
                        Send-MailMessage -From \$MailFrom -To \$MailTo -Subject \$MailSubject -Body \$MailBody -SmtpServer \$MailServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential \$MailUsername, (ConvertTo-SecureString -AsPlainText \$MailPassword -Force))
                    """
                    powershell(powershellScript)
                }
            }
        }
        
        stage('Deploy Staging') {
            steps {
                echo 'Deploying to staging environment...'
            }
        }
        
        stage('Integration Test') {
            steps {
                echo 'Running integration tests...'
            }
post {
                
                success {
                    emailext  subject: 'Unit Test Status - Success', 
                              body: 'Unit Test has been completed successfully.', 
                              to: "arsh4765.be22@chitkara.edu.in",
                              attachLog: true
                }
                failure {
                    emailext subject: 'Unit Test Status - Failure', 
                              body: 'Unit Test has failed.', 
                             to: "arsh4765.be22@chitkara.edu.in",
                              attachLog: true
                }
            }
        }
        
        stage('Deploy Production') {
            steps {
                echo 'Deploying to production environment...'
            }
        }
    }
    
    post {
        success {
            script {
                def powershellScript = """
                    \$MailServer = "smtp.example.com"
                    \$MailFrom = "sender@example.com"
                    \$MailTo = "recipient@example.com"
                    \$MailSubject = "Pipeline Success"
                    \$MailBody = "Pipeline executed successfully."
                    \$MailUsername = "yourusername"
                    \$MailPassword = ""
    
                    Send-MailMessage -From \$MailFrom -To \$MailTo -Subject \$MailSubject -Body \$MailBody -SmtpServer \$MailServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential \$MailUsername, (ConvertTo-SecureString -AsPlainText \$MailPassword -Force))
                """
                powershell(powershellScript)
            }
            echo 'Pipeline executed successfully!'
        }
        failure {
            script {
                def powershellScript = """
                    \$MailServer = "smtp.example.com"
                    \$MailFrom = "sender@example.com"
                    \$MailTo = "recipient@example.com"
                    \$MailSubject = "Pipeline Failure"
                    \$MailBody = "Pipeline failed to execute."
                    \$MailUsername = "yourusername"
                    \$MailPassword = ""
    
                    Send-MailMessage -From \$MailFrom -To \$MailTo -Subject \$MailSubject -Body \$MailBody -SmtpServer \$MailServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential \$MailUsername, (ConvertTo-SecureString -AsPlainText \$MailPassword -Force))
                """
                powershell(powershellScript)
            }
            echo 'Pipeline execution failed! Please check for errors.'
        }
    }
}
