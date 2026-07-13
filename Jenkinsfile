pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                 script {
                    dir('src') {
                sh 'docker build -t ravinaclouddevops/cartservice:latest .'
             }
          }
        }
        
        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-cred', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                    sh 'echo "$PASSWORD" | docker login -u "$USERNAME" --password-stdin'
                }
            }
        }

        stage('Push') {
            steps {
                sh 'docker push ravinaclouddevops/cartservice:latest'
            }
        }
    }
}
