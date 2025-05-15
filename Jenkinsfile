pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'jayanavekar2@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Starting Build Stage...'
                bat '''
                    echo Building the project Maven / Gradle / MSBuild / npm...
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Starting Test Stage JUnit / NUnit / Selenium / Jest / Mocha..'
               
            }
            post {
                success {
                    emailext(
                        to: "${env.EMAIL_RECIPIENT}",
                        subject: "Test Stage - SUCCESS",
                        body: "The Test stage completed successfully. Please find the log attached.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "${env.EMAIL_RECIPIENT}",
                        subject: "Test Stage - FAILURE",
                        body: "The Test stage failed. Please check the attached logs.",
                        attachLog: true
                    )
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Starting Security Scan Stage. SonarQube / OWASP Dependency-Check / Snyk..'
                bat '''
                    echo Scanning for vulnerabilities...
                    
                '''
            }
            post {
                success {
                    emailext(
                        to: "${env.EMAIL_RECIPIENT}",
                        subject: "Security Scan - SUCCESS",
                        body: "The Security Scan completed successfully. Please find the log attached.",
                        attachLog: true
                    )
                }
                failure {
                    emailext(
                        to: "${env.EMAIL_RECIPIENT}",
                        subject: "Security Scan - FAILURE",
                        body: "The Security Scan failed. Please check the attached logs.",
                        attachLog: true
                    )
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Starting Deployment Stage 	Docker / Ansible / Helm / Kubernetes / SCP...'
                bat '''
                    echo Deploying application...
                '''
            }
        }
    }
}
