pipeline {
    agent any 
    stages {
        stage('Example Build') {
            steps {
                echo 'Hello'
                git url: 'https://github.com/beomchankim/azure-voting-app-redis.git',
                    branch: 'master',
                    credentialsId: 'jenkins'
                // git pull
            }
            
            post {
                success {
                    echo 'Success'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                echo 'Deploy'

            }
        }
    }
}
