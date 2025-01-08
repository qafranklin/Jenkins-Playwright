pipeline {
    agent any

    environment {
        NODE_HOME = 'C:\\Program Files\\nodejs'  // Adjust path to your Node.js installation (note the double backslashes)
        PATH = "${NODE_HOME};${env.PATH}"  // Ensure Node.js is added to the PATH for Jenkins
    }

    stages {
        stage('Install Dependencies') {
            steps {
                script {
                    bat 'npm install -g playwright'  // Install Playwright globally using 'bat' for Windows
                    bat 'npm install'  // Install project dependencies
                }
            }
        }

        stage('Run Playwright Tests') {
            steps {
                script {
                    bat 'npx playwright test'  // Run Playwright tests using 'bat' for Windows
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }

        success {
            echo 'Playwright tests ran successfully.'
        }

        failure {
            echo 'Playwright tests failed.'
        }
    }
}
