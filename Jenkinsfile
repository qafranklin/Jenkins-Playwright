pipeline {
    agent any

    environment {
        NODE_HOME = '/usr/local/bin/node'  // Path to Node.js if required
        PATH = "${NODE_HOME}:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                // Check out the repository
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install Node.js and dependencies
                    sh 'npm install'
                }
            }
        }

        stage('Run Playwright Tests') {
            steps {
                script {
                    // Run Playwright tests using npx
                    sh 'npx playwright test'
                }
            }
        }

        stage('Archive Test Results') {
            steps {
                // Optionally, you can archive the test results
                archiveArtifacts artifacts: '**/test-results/**/*.xml', allowEmptyArchive: true
            }
        }
    }

    post {
        always {
            // Clean up actions after the test, if any
        }

        success {
            echo 'Playwright tests passed!'
        }

        failure {
            echo 'Playwright tests failed!'
        }
    }
}
