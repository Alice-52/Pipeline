pipeline {
    agent { docker { image 'python:3.14.6-alpine3.24' } }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
            }
        }
        stage('test') {
            steps {
                sh 'echo "Тесты прошли (понарошку)"'
            }
        }
    }
    post {
        success {
            echo 'Pipeline отработал успешненько!'
        }
        failure {
            echo 'Что-то я наворотила'
        }
    }
}
