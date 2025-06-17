pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-C', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://1DBA839A1E85D696A6144CCE4E390869.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-c', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://1DBA839A1E85D696A6144CCE4E390869.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
