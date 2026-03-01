pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                bat 'docker build -t python-devops-app .'
            }
        }

        stage('Code Review') {
            steps {
                bat 'docker run --rm python-devops-app flake8 app.py'
            }
        }

        stage('Test') {
            steps {
                bat 'docker run --rm python-devops-app pytest'
            }
        }

        stage('Deploy Localhost') {
            steps {
                bat '''
                docker rm -f python-devops-app-container >nul 2>&1 || exit /b 0
                docker run -d -p 5000:5000 --name python-devops-app-container python-devops-app
                '''
            }
        }
    }

    post {
        success {
            echo "PIPELINE SUCCESS"
        }
    }
}