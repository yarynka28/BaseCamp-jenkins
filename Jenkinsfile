pipeline {
    agent any
    environment{
        TOKEN = credentials('TOKEN_ID')
        CHAT = credentials('CHAT_ID')
    }
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
                bat  ('curl -s -X POST https://api.telegram.org/bot$TOKEN/sendMessage -d chat_id=$CHAT -d text="Successful deployment on MASTER branch"')
                }
            }
        }
        
    }
