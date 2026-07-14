pipeline {
    agent { docker { image 'python:3.14.6-alpine3.24' } }
    environment {
        APP_NAME = 'my-python-app'
        VERSION = '0.1'
    }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
                sh 'echo "Собираем $APP_NAME версии $VERSION"'
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
