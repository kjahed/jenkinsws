pipeline {
    agent any
    stages {
        stage("Init") {
            steps {
                sh "python -m venv .venv"
                sh ". .venv/bin/activate && pip install -r requirements.txt"
            }
        }

        stage("Test") {
            sh ". .venv/bin/activate && pytest tests/"
        }
    }
}