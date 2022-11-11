pipeline {
    agent any 
    environment {
            DOCKERHUB_CREDENTIALS=credentials('huysanti123')

    stages {
         stage('Preparation') {
            steps {
                echo 'BE PREPARED!'
                sh 'docker rm -f cowsay-container'
            }
        }
        

       stage('Build') {
            steps {
                git (
                    branch: 'main',
                    url: 'https://github.com/JustAbusiness/huy-jenkins.git'
                    )
                dir('code') {
                  sh 'docker build -t cowsay .'
                }
                sh 'ls'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run -d --rm -p 8081:8080 --name cowsay-container cowsay'
                sh 'sleep 10'
                sh 'docker ps -a'
                sh 'curl docker:8081'
            }
        }
        
        stage('Login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        
        stage('Push') {
            steps {
                sh 'docker push docker push ngochuy2703/cowsay:tagnam"
            }
        }
            
    }

    post {
        always {
            sh 'docker logout'
    }
  }
}
