pipeline {
    agent any

    environment {
        KUBECONFIG_FILE = "${env.WORKSPACE}/kubeconfig"
    }

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker', usernameVariable: 'nagauppu', passwordVariable: 'NANAamma@1023')]) { 
                    sh 'echo $NANAamma@1023 | docker login -u $nagauppu --password-stdin'
                        kubectl apply -f deployment-service.yml
                    '''
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withCredentials([string(credentialsId: 'docker', variable: 'KUBECONFIG_CONTENT')]) {
                    sh '''
                        echo "$KUBECONFIG_CONTENT" | base64 -d > $KUBECONFIG_FILE
                        export KUBECONFIG=$KUBECONFIG_FILE
                        kubectl get svc -n webapps
                    '''
                }
            }
        }
    }
}



