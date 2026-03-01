pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                bat 'py -m pip install -r requirements.txt'
            }
        }

        stage('Code Review') {
            steps {
                bat 'py -m flake8 app.py'
            }
        }

        stage('Test') {
            steps {
                bat 'py -m pytest'
            }
        }

        stage('Deploy Localhost') {
            steps {
                bat 'start /B py app.py'
            }
        }
    }
}