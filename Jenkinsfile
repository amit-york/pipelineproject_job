pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                echo '📦 Installing Node dependencies...'
                sh 'npm install'
            }
        }

        stage('Start Express Server in Background') {
            steps {
                echo '🚀 Starting Express server...'
                sh 'nohup npm start > server.log 2>&1 &'
            }
        }

        stage('Test Server Running') {
            steps {
                echo '🔍 Testing the running server...'
                sh 'sleep 2'
                sh 'curl http://localhost:3000'
            }
        }
    }

    post {
        always {
            echo '📋 Pipeline completed.'
        }
    }
}
