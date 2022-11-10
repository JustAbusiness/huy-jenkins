pipeline {
    agent any 

    stages {
        stage('Build') {
            steps {
                sh "docker build -t cowsay ."
            }
        }
        

        stage('Test') {
            steps {
               sh "docker run -d --rm -p 8081:8080 --name cowsay-container cowsay " 
        }
        }

        stage('Stop') {
            steps {
                sh "sleep 10"
                sh "curl docker:8081"
            }
        }

        stage('Publish') {
            steps {
                
            }
        }
    
    }


}