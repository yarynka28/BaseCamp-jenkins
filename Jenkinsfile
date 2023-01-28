pipeline {
    agent any
    environment{
        TOKEN_ID = credentials("botId")
        CHAT_ID = credentials("chatId")
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
                bat  ("curl -s -X POST https://api.telegram.org/bot${TOKEN_ID}/sendMessage -d chat_id=${CHAT_ID} -d parse_mode=markdown -d text='*Full project name*: ${env.JOB_NAME} \n*Branch*: [$GIT_BRANCH]($GIT_URL) \n*Build* : [OK](${BUILD_URL}consoleFull)'")
                }
            }
        }
        
    }
