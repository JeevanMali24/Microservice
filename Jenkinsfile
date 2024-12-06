pipeline {
    agent any

    stages {
        
        
        stage('deploy to kuberentes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://B01887DE2DB3C2257D1C8F1E6F5D37BD.gr7.ap-south-1.eks.amazonaws.com']])
               { sh 'kubectl apply -f deployment-service.yml' }
            }
        }
        stage('verify of kuberenetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: ' EKS-1', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://B01887DE2DB3C2257D1C8F1E6F5D37BD.gr7.ap-south-1.eks.amazonaws.com']])
                { sh 'kubectl get svc -n webapps' }
            }
        }
    }
}
