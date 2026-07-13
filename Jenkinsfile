pipeline {
    agent any

    stages {
        stage('Build & Tag Docker Image') {
            steps {
                script {
                    dir('src') {
                        sh "docker build -t adijaiswal/cartservice:latest ."
                        
                        }
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
    }
}
