pipeline {
    agent any

    environment {
        EMAIL_RECIPIENT = 'jayanavekar2@gmailcom'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Starting Build Staage...'
                bat 'echo Building the project...'
            }
        }

        stage('Test') {
            steps {
                echo 'Starting Test Stage...'
                bat 'echo Running tests... && timeout /t 2'
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
                echo 'Starting Security Scan Stage...'
                bat 'echo Scanning for vulnerabilities... && timeout /t 2'
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
                echo 'Starting Deployment Stage...'
                bat 'echo Deploying application...'
            }
        }
    }
}
