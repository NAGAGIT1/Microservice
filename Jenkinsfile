pipeline {
    agent any

    environment {
        KUBECONFIG_FILE = "${env.WORKSPACE}/kubeconfig"
    }

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh """
                        echo \$DOCKER_PASS | docker login -u \$DOCKER_USER --password-stdin
                        kubectl apply -f deployment-service.yml
                    """
                }
            }
        }

        stage('Verify Deployment') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    sh """
                        echo \$DOCKER_PASS | docker login -u \$DOCKER_USER --password-stdin
                        kubectl get svc -n webapps
                    """
                }
            }
        }
    }
}




