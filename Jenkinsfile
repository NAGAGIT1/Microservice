pipeline {
    agent any

    environment {
        KUBECONFIG_FILE = "${env.WORKSPACE}/kubeconfig"
    }

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withCredentials([string(credentialsId: 'kubeconfig-eks', variable: 'KUBECONFIG_CONTENT')]) {
                    sh '''
                        echo "$KUBECONFIG_CONTENT" > $KUBECONFIG_FILE
                        export KUBECONFIG=$KUBECONFIG_FILE
                        kubectl apply -f deployment-service.yml
                    '''
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withCredentials([string(credentialsId: 'kubeconfig-eks', variable: 'KUBECONFIG_CONTENT')]) {
                    sh '''
                        echo "$KUBECONFIG_CONTENT" > $KUBECONFIG_FILE
                        export KUBECONFIG=$KUBECONFIG_FILE
                        kubectl get svc -n webapps
                    '''
                }
            }
        }
    }
}


