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
        }
        failure {
            echo 'Build failed.'
        }
    }
}
