pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                echo 'Dependency installation...'
                echo 'Building application...'
                git branch: 'main', url: 'https://github.com/ARSHSUU/task6'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing...'
                
                script {
                    def powershellCommand = """
                        \$SMTPServer = "smtp.gmail.com"
                        \$SMTPFrom = "example@gmail.com"
                        \$SMTPTo = "example@gmail.com"
                        \$SMTPSubject = "Test success."
                        \$SMTPBody = "Test successful."
                        \$SMTPUsername = "example@gmail.com"
                        \$SMTPPassword = ""
    
                        Send-MailMessage -From \$SMTPFrom -to \$SMTPTo -Subject \$SMTPSubject -Body \$SMTPBody -SmtpServer \$SMTPServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential \$SMTPUsername, (ConvertTo-SecureString -AsPlainText \$SMTPPassword -Force))
                    """
                    powershell(powershellCommand)
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Code analysis...'
            }
        }
        stage('Security') {
            steps {
                echo 'Security scans...'
                
                script {
                    def powershellCommand = """
                        \$SMTPServer = "smtp.gmail.com"
                        \$SMTPFrom = "example@gmail.com"
                        \$SMTPTo = "example@gmail.com"
                        \$SMTPSubject = "Security checks passed."
                        \$SMTPBody = "Pipeline cleared security checks."
                        \$SMTPUsername = "example@gmail.com"
                        \$SMTPPassword = ""
    
                        Send-MailMessage -From \$SMTPFrom -to \$SMTPTo -Subject \$SMTPSubject -Body \$SMTPBody -SmtpServer \$SMTPServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential \$SMTPUsername, (ConvertTo-SecureString -AsPlainText \$SMTPPassword -Force))
                    """
                    powershell(powershellCommand)
                }
            }
        }
        
        stage('Deploy Staging') {
            steps {
                echo 'Staging deployment...'
            }
        }
        
        stage('Integration Test') {
            steps {
                echo 'Integration testing...'
            }
        }
        
        stage('Deploy Production') {
            steps {
                echo 'Production deployment...'
            }
        }
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
    post {
        success {
            script {
                def powershellCommand = """
                    \$SMTPServer = "smtp.gmail.com"
                    \$SMTPFrom = "example@gmail.com"
                    \$SMTPTo = "example@gmail.com"
                    \$SMTPSubject = "Success."
                    \$SMTPBody = "Pipeline executed successfully."
                    \$SMTPUsername = "example@gmail.com"
                    \$SMTPPassword = ""
    
                    Send-MailMessage -From \$SMTPFrom -to \$SMTPTo -Subject \$SMTPSubject -Body \$SMTPBody -SmtpServer \$SMTPServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential \$SMTPUsername, (ConvertTo-SecureString -AsPlainText \$SMTPPassword -Force))
                """
                powershell(powershellCommand)
            }
            echo 'Success!'
        }
        failure {
            script {
                def powershellCommand = """
                    \$SMTPServer = "smtp.gmail.com"
                    \$SMTPFrom = "example@gmail.com"
                    \$SMTPTo = "example@gmail.com"
                    \$SMTPSubject = "Failure"
                    \$SMTPBody = "Pipeline failed to execute."
                    \$SMTPUsername = "example@gmail.com"
                    \$SMTPPassword = ""
    
                    Send-MailMessage -From \$SMTPFrom -to \$SMTPTo -Subject \$SMTPSubject -Body \$SMTPBody -SmtpServer \$SMTPServer -UseSsl -Port 587 -Credential (New-Object System.Management.Automation.PSCredential \$SMTPUsername, (ConvertTo-SecureString -AsPlainText \$SMTPPassword -Force))
                """
                powershell(powershellCommand)
            }
            echo 'Failure! Check for errors.'
        }
    }
}
