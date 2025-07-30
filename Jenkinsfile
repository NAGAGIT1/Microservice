pipeline {
    agent any

    environment {
        CLUSTER_NAME = 'EKS'         // Your EKS cluster name
        AWS_REGION = 'us-east-2'     // Your AWS region
    }

    stages {
        stage('Configure Kubeconfig') {
            steps {
                sh '''
                aws eks update-kubeconfig --name $CLUSTER_NAME --region $AWS_REGION
                '''
            }
        }

        stage('Deploy To Kubernetes') {
            steps {
                sh 'kubectl apply -f deployment-service.yml'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'kubectl get svc -n default'
            }
        }
    }
}

