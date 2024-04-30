pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "https://github.com/mohansaikiran/jenkins_config"
    }

    stages {
        stage('Build') {
            steps {
                echo "Fetch the source code from the directory path specified by $DIRECTORY_PATH"
                echo "Compile the code and generate any necessary artifacts"
            }
        }
        stage('Test') {
            steps {
                echo "Unit Tests"
                echo "Integration Tests"
            }
        }
        stage('Code Quality Check') {
            steps {
                echo "Check the quality of the code"
            }
        }
        stage('Deploy') {
            steps {
                echo "Deploying the application to a testing environment specified by the name $TESTING_ENVIRONMENT"
            }
        }
        stage('Approval') {
            steps {
                echo "Waiting for approval"
                sleep(10)
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying the application to production environment specified by the name $PRODUCTION_ENVIRONMENT"
            }
        }
    }
}