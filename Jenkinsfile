pipeline {
    agent any
    
    environment {
        WEB_IMAGE_NAME = "jenkins/inbound-agent:v${BUILD_NUMBER}"
    }
    stages {
        stage('Git Pull') {
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
        
        stage('Build') {
            steps {
                echo 'Build'
                sh 'docker build -t ${WEB_IMAGE_NAME} ./azure-vote'
            }
            post {
                success {
                    echo 'Success'
                }
            }
        
        }
        
        stage('Login') {
            steps {
                echo 'Login'
                sh 'docker login -u ${DOCKER_ID} -p ${DOCKER_PASSWORD}'
            }
            post {
                success {
                    echo 'Success'
                }
            }
        }
        
        stage('Push') {
            steps {
                echo 'Push'
                sh 'docker push ${WEB_IMAGE_NAME}'
            }
            post {
                success {
                    echo 'Success'
                }
            }
        }
    }
}
