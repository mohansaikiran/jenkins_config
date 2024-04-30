pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "https://github.com/jenkins_source_code"
        TESTING_ENVIRONMENT = "Jenkins_test_env_Mohan"
        PRODUCTION_ENVIRONMENT = "Jenkins_prod_env_Mohan"
    }

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
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Analysing the code using ESLint..."
            }
        }
        stage('Security scan') {
            steps {
                def logFilePath = "${WORKSPACE}/security-output.log"
                echo "Performing security scans using Veracode for vulnerabilities..."

                sh """ 
                    echo 'Performing security scans using Veracode for vulnerabilities...' >> ${logFilePath}
                    echo 'Security checks completed and no vulnerabilities found' >> ${logFilePath}
                """
            }
            post {
                success {
                    emailext subject: "Security Scan Status: SUCCESS",
                            body: "The security scan completed successfully",
                            to:"kiranms20@gmail.com",
                            attachmentsPattern: "security-output.log"
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