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
                 taskkill /F /IM python.exe >nul 2>&1 || exit /b 0
                 cmd /c start "FlaskApp" "%PYTHON%" app.py
                 '''
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