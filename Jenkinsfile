pipeline {
    agent { 
        dockerContainer { image 'python:3.11' }
    }
    stages {
        stage("Init") {
            steps {
                sh "pip install -r requirements.txt"
            }
        }

        stage("Test") {
            steps {
                sh "pytest tests/ --junitxml=reports/junit.xml"
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