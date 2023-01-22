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
                curl -s -X POST https://api.telegram.org/bot${TOKENID}/sendMessage -d chat_id=${CHAT_ID} -d parse_mode=markdown -d text='*Branch*: ${env.BRANCH_NAME} *Build* ${env.BUILD_NUMBER} *Result* ${currentBuild.currentResult}'
                """)
            }
        }
    }
}
