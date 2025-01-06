pipeline {
    agent any
    environment {
        NODE_HOME = tool name: 'Node 16', type: 'NodeJS'
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
                    sh 'npm install'
                    sh 'npx playwright install'
                }
            }
        }
        stage('Run Playwright Tests') {
            steps {
                script {
                    sh 'node test.js'  // Adjust this to your test script filename
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
