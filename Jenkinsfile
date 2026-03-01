pipeline {
    agent any

    environment {
        PYTHON = "C:\\Users\\LENOVO\\AppData\\Local\\Python\\pythoncore-3.14-64\\python.exe"
    }

    stages {

        stage('Build') {
            steps {
                bat "\"%PYTHON%\" -m pip install -r requirements.txt"
            }
        }

        stage('Code Review') {
            steps {
                bat "\"%PYTHON%\" -m flake8 app.py"
            }
        }

        stage('Test') {
            steps {
                bat "\"%PYTHON%\" -m pytest"
            }
        }

        stage('Deploy Localhost') {
            steps {
                bat '''
                cd /d C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\python-devops-pipeline
                powershell -Command "Start-Process '%PYTHON%' -ArgumentList 'app.py' -WindowStyle Hidden"
                '''
            }
        }
    }

    post {
        success {
            echo "PIPELINE SUCCESS"
        }
        failure {
            echo "PIPELINE FAILED"
        }
    }
}