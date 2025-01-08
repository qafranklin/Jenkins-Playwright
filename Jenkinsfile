pipeline {
    agent any
    environment {
        NODE_HOME = tool name: 'Node 16', type: 'NodeJS'  // Ensure Node 16 is configured in Jenkins
        PATH = "${NODE_HOME}/bin:${env.PATH}"  // Add Node.js to the PATH environment variable
    }
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/qafranklin/Jenkins-Playwright.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    // Use bat to run npm and playwright installation on Windows
                    bat 'npm install'  // Equivalent to sh 'npm install' in Linux/Unix
                    bat 'npx playwright install'  // Equivalent to sh 'npx playwright install'
                }
            }
        }
        stage('Run Playwright Tests') {
            steps {
                script {
                    // Run the Playwright tests using Node.js on Windows
                    bat 'node test.js'  // Equivalent to sh 'node test.js'
                }
            }
        }
    }
    post {
        always {
            echo 'Cleaning up...'
        }
    }
}
