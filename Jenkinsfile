pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                bat 'python -m pip install -r requirements.txt'
            }
        }

        stage('Code Review') {
            steps {
                bat 'flake8 app.py'
            }
        }

        stage('Test') {
            steps {
                bat 'pytest'
            }
        }

        stage('Deploy Localhost') {
            steps {
                bat 'start /B python app.py'
            }
        }
    }
}