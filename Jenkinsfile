pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t ravinaclouddevops/paymentservice:latest .'
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
                sh 'docker push ravinaclouddevops/paymentservice:latest'
            }
        }
    }
}
