pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                echo 'Applying Kubernetes deployment and service YAML'
                sh "kubectl apply -f deployment-service.yml"
            }
        }
        
        stage('Verify Deployment') {
            steps {
                echo 'Checking Kubernetes services in default namespace'
                sh "kubectl get svc -n default"
            }
        }
    }
    
    post {
        always {
            echo 'Pipeline completed.'
        }
        failure {
            echo 'Pipeline failed. Please check the logs.'
        }
    }
}

