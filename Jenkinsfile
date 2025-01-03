pipeline {
    agent any

    environment {
        // Define your environment variables if needed (e.g., for Playwright)
        PLAYWRIGHT_BROWSERS_PATH = '/path/to/your/browsers' // Optional: Set this if using custom browser installations
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from repository
                git 'https://github.com/qafranklin/Jenkins-Playwright.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install Node.js dependencies including Playwright
                script {
                    // Make sure to install NodeJS if not already done
                    sh 'npm install'
                }
            }
        }

        stage('Run Playwright Tests') {
            steps {
                // Run Playwright tests
                script {
                    // Execute Playwright tests
                    sh 'npx playwright test'
                }
            }
        }

        stage('Archive Test Results') {
            steps {
                // Archive the test results for review
                junit '**/test-results/*.xml' // Adjust to where your test results are generated
            }
        }
    }

}