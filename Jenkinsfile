pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        } 
        stage('Deploy only on MASTER') {
            when {
                branch 'master'
            }
            steps {
                echo 'Deploying only on MASTER'
            }
        }
        stage('Notification') {
            steps {
                telegramSend(message: 'Deploying only on MASTER succesfull')
            }
        }
    }
}
