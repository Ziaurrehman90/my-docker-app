pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Ziaurrehman90/my-docker-app'
            }
        }

        stage('Setup') {
            steps {
                sh '''
                  echo "Installing Python..."
                  apt-get update
                  apt-get install -y python3 python3-pip
                '''
            }
        }

        stage('Build') {
            steps {
                sh 'echo Building app...'
                sh 'python3 --version'
                sh 'if [ -f app.py ]; then python3 app.py; else echo "No app.py found"; fi'
            }
        }

        stage('Test') {
            steps {
                sh 'echo Running tests...'
                sh 'if [ -f test_app.py ]; then python3 -m unittest test_app.py; else echo "No tests found"; fi'
            }
        }
    }
}
