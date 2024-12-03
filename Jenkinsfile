pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://4CC4F232E081C7AEEC113CCEB54EF986.sk1.ap-south-1.eks.amazonaws.com']]) {
                sh 'kubectl apply -f deployment-service.yml'
                sleep 60
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://4CC4F232E081C7AEEC113CCEB54EF986.sk1.ap-south-1.eks.amazonaws.com']]) {
                sh 'kubectl get all -n webapps'
                }
            }
        }
    }
}
