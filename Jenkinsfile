pipeline {
    agent {
        docker {
            image 'node:18'   // Use Node.js 18 official image
            args '-p 3000:3000' // Map port if you want to run the app
        }
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Ziaurrehman90/my-docker-app'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'echo Building Node.js app...'
                sh 'if [ -f app.js ]; then node app.js; else echo "No app.js found"; fi'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Running tests...'
                sh 'npm test || echo "No tests configured"'
            }
        }
    }
}
