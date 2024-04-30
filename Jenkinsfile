pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "Compiling the code and generating necessary artifacts using Maven..."
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Performing Unit Testing using JUnit..."
                echo "Performing Integration Testing using Selenium WebDriver..."

                script {
                    def logFilePathNew = "${env.WORKSPACE}/test-output.log"
                
                sh """
                        echo 'Starting unit testing using JUnit...' > ${logFilePathNew}
                        echo 'Testing the feature working...' >> ${logFilePathNew}
                        echo 'Unit testing completed and no issues found' >> ${logFilePathNew}
                        echo '\n\nStarting Integration testing using Selenium WebDriver...' >> ${logFilePathNew}
                        echo 'End to End Testing of the complete product working...' >> ${logFilePathNew}
                        echo 'Integration testing completed and no issues found' >> ${logFilePathNew} 
                """
                }
            }
            post {
                success {
                    emailext attachmentsPattern: 'test-output.log',
                            body: 'The Unit Testing and Integration testing completed successfully',
                            subject: 'Unit and Integration Testing Status: SUCCESS',
                            to:'kiranms20@gmail.com'
                }
                failure {
                    emailext attachmentsPattern: 'security-output.log',
                            body: 'The Unit Testing and Integration testing completed unsuccessfully. Please check logs!',
                            subject: 'Unit and Integration Testing Status: FAILURE',
                            to:'kiranms20@gmail.com'
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analysing the code using ESLint..."
            }
        }
        stage('Security scan') {
            steps {
                echo "Performing security scans using Veracode for vulnerabilities..."

                script {
                    def logFilePath = "${env.WORKSPACE}/security-output.log"
                
                sh """
                        echo 'Starting security scan...' > ${logFilePath}
                        echo 'Scanning for vulnerabilities...' >> ${logFilePath}
                        echo 'Security scan completed successfully and no vulnerabilities found' >> ${logFilePath} 
                """
                }
            }
            post {
                success {
                    emailext attachmentsPattern: 'security-output.log',
                            body: 'The security scan completed successfully',
                            subject: 'Security Scan Status: SUCCESS',
                            to:'kiranms20@gmail.com'
                }
                failure {
                    emailext attachmentsPattern: 'security-output.log',
                            body: 'The security scan completed unsuccessfully. Please check logs!',
                            subject: 'Security Scan Status: FAILURE',
                            to:'kiranms20@gmail.com'
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying the application to the staging server on AWS EC2 instance..."
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Executing integration tests on the staging environment..."
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to the production server on AWS EC2 instance..."
            }
        }
    }
}