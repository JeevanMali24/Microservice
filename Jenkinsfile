pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('git checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/JeevanMali24/Microservice.git'
            }
        }
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
