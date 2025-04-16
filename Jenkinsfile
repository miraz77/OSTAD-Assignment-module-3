pipeline {
    agent any

    tools {
        nodejs 'NodeJS 22' 
    }

    stages {
        stage('Clone') {
            steps {
                git branch: 'main', url: 'https://github.com/miraz77/OSTAD-Assignment-module-3.git'
            }
        }

        stage('Prepare') {
            steps {
                sh 'mkdir -p test-results'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                sh 'npm run check'
            }
        }
    }

    post {
        always {
            junit 'test-results/results.xml'
        }
        success {
            echo 'Build succeeded.'
            echo '[Slack Placeholder] Build SUCCESS: Would notify #ci-notifications'
         // slackSend (color: '#36a64f', message: "✅ Build SUCCESS: ${env.JOB_NAME} #${env.BUILD_NUMBER}\n${env.BUILD_URL}")
        }
        failure {
            echo 'Build failed.'
            echo '[Slack Placeholder] Build FAILED: Would notify #ci-notifications'
         // slackSend (color: '#ff0000', message: "❌ Build FAILED: ${env.JOB_NAME} #${env.BUILD_NUMBER}\n${env.BUILD_URL}")
        }
    }
}
