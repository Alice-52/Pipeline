pipeline {
    agent { docker { image 'python:3.14.6-alpine3.24' } }
    parameters {
        string(name: 'GREETING', defaultValue: 'Hey', description: 'Неформально поздоровались на англицком')
        choice(name: 'ENVIRONMENT', choices: ['dev','staging','prod'], description: 'Blue/Green deployment means: Blue does not work, Green is even worse')
        booleanParam(name: 'RUN_TESTS', defaultValue: true, description: 'Тестируем ли?!')
    }
    environment {
        APP_NAME = 'my-python-app'
        VERSION = '0.1'
    }
    stages {
        stage('build') {
            steps {
                sh 'python --version'
                sh 'echo "Собираем $APP_NAME версии $VERSION"'
                echo "${params.GREETING} man!"
                echo "Хотите шутку про Blue/Green? ${params.ENVIRONMENT}"
            }
        }
        stage('test') {
            when {
                expression { params.RUN_TESTS == true }
            }
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
