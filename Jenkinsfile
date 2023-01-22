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
                echo 'Deploying only on MASTER..'
            }
        }
        stage('Notification') {
            steps {
                echo 'Notification TelegramBot..'
            }
        }
        
    }
    post {
        always {
            withCredentials([string(credentialsId: 'TOKEN_ID', variable: 'TOKEN_ID'), string(credentialsId: 'CHAT_ID', variable: 'CHAT_ID')]) {
                sh  ("""
                curl -s -X POST https://api.telegram.org/bot${TOKEN_ID}/sendMessage -d chat_id=${CHAT_ID} -d text='text'
            }
        }
    }
}
