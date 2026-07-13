pipeline {
    agent any

    stages {
        stage('deployement to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://D8DACF4F6D230EBBA5F32A9F93B9499D.gr7.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl apply -f deployment-service.yml"
                   slee 60
                }
            }
        }
        stage('verify deployement') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://D8DACF4F6D230EBBA5F32A9F93B9499D.gr7.ap-south-1.eks.amazonaws.com']]) {
                   sh "kubectl get all -n webapps"
                }
            }
        }
    }
}
