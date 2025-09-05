pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Ziaurrehman90/my-docker-app',
                    credentialsId: 'ecf815ab-0b0f-442a-9767-d2b76edddaf6'
            }
        }

        stage('Build') {
            steps {
                sh 'echo Building app...'
                sh 'python3 --version || python --version'
                sh 'if [ -f app.py ]; then python3 app.py || python app.py; else echo "No app.py found"; fi'
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
