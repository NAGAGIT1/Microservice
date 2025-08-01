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
                withCredentials([usernamePassword(credentialsId: 'docker', usernameVariable: 'nagauppu', passwordVariable: 'NANAamma@1023')]) { 
                    sh 'echo $NANAamma@1023 | docker login -u $nagauppu --password-stdin'
                        kubectl get svc -n webapps
                    '''
                }
            }
        }
    }
}



