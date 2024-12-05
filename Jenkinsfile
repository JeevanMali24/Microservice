pipeline {
    agent any

    stages {
        stage('deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://072A5EB96EDAA2097FDDDBE9FAA4A648.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh 'kubectl apply -f deployment-service.yml'
                }
            }
        }
        stage('verify deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://072A5EB96EDAA2097FDDDBE9FAA4A648.gr7.ap-south-1.eks.amazonaws.com']]) {
                sh 'kubectl get svc -n webapps'
                }
            }
        }
    }
}
