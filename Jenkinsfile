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
                sh  ("""
                curl -s -X POST https://api.telegram.org/bot5967703246:AAHBDJQTLJwifrbJCQxC6Ott-8inb3mkpdI/sendMessage -d chat_id=-1001557268181 -d parse_mode=markdown -d text='*Branch*: ${env.BRANCH_NAME} *Build* ${env.BUILD_NUMBER} *Result* ${currentBuild.currentResult}'
                """)
            }
        }
    }
}
