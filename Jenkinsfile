pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh 'python -m pip install -r requirements.txt'
            }
        }

        stage('Code Review') {
            steps {
                sh 'flake8 app.py'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest'
            }
        }

        stage('Deploy Localhost') {
            steps {
                sh 'python app.py'
            }
        }
    }
}