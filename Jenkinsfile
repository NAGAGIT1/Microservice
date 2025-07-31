pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://18597938C0775F021940DA658A3977B6.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://18597938C0775F021940DA658A3977B6.gr7.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
