pipeline {
    agent any

    stages {
        
        
        stage('deploy to kuberentes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://993B5EFF4430553DE7E1622DCB838BD0.gr7.ap-south-1.eks.amazonaws.com']])
               { sh 'kubectl apply -f deployment-service.yml' }
            }
        }
        stage('verify of kuberenetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://993B5EFF4430553DE7E1622DCB838BD0.gr7.ap-south-1.eks.amazonaws.com']])
                { sh 'kubectl get svc -n webapps' }
            }
        }
    }
}
