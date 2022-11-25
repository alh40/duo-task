pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh '''
                docker-compose build
                '''
            }
        }
        stage('Deploy') {
            steps {
                sh'''
                ssh -i "~/.ssh/id_rsa" jenkins@34.175.65.57 << EOF
                rm -rf duo-task
                git clone https://github.com/alh40/duo-task.git
                cd duo-task
                docker-compose down
                docker-compose up -d
                '''
            }
        }
    }
}