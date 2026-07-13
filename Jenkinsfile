pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t ravinaclouddevops/recommendationservice:latest .'
            }
        }

        stage('Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-cred', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push') {
            steps {
                sh 'docker push ravinaclouddevops/recommendationservice:latest'
            }
        }
    }
}
