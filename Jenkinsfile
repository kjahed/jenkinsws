pipeline {
    agent { label 'python'}
    stages {
        stage("Init") {
            steps {
                sh "python -m venv .venv"
                sh ". .venv/bin/activate && pip install -r requirements.txt"
            }
        }

        stage("Test") {
            steps {
                sh ". .venv/bin/activate && pytest tests/ --junitxml=reports/junit.xml"
            }
        }
    }

    post {
        always {
            junit 'reports/junit.xml'
            archiveArtifacts artifacts: 'reports/**', allowEmptyArchive: true
        }
    }
}