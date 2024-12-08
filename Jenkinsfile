pipeline {
    agent any

    stages {
        stage('deploy to kubernetes') {
            steps {
             withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://678D754BCF0D0E8BA410E9B076F0BD19.gr7.ap-south-1.eks.amazonaws.com']]) {
             sh 'kubectl apply -f deployment-service.yml'   
                }   
            }
        }
        stage('deploy to kubernetes') {
            steps {
             withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://678D754BCF0D0E8BA410E9B076F0BD19.gr7.ap-south-1.eks.amazonaws.com']]) {
             sh 'kubectl get svc -n webapps'   
                }   
            }
        }
    }
}
