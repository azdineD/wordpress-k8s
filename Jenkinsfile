pipeline {
    agent any

    environment {
        KUBECONFIG = '/root/.kube/config'
    }

    stages {
        stage('Déploiement WordPress') {
            steps {
                sh 'kubectl apply -f wordpress-pvc.yaml'
                sh 'kubectl apply -f wordpress-deployment.yaml'
                sh 'kubectl apply -f wordpress-service.yaml'
            }
        }

        stage('Vérification') {
            steps {
                sh 'kubectl get pods'
                sh 'kubectl get svc'
            }
        }
    }
}
