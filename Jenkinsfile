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
        stage('conditional check') {
            steps {
                script {
                    def today = new Date()
                    def dayName = today.format('EEEE')
                    echo "Сегодня вот такой вот день: ${dayName}"

                    if (dayName == 'Friday' || dayName == 'Saturday' || dayName == 'Sunday') {
                        echo "ВЫХОДНЫЕ - ураураура!!!"
                    } else {
                        echo "Работаемработаем - рабочие будни"
                    }
                }
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
