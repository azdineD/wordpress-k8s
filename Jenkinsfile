pipeline {
    agent any

        stage('Déploiement WordPress') {
            steps {
                script {
                    sh 'kubectl apply -f wordpress-pvc.yaml'
                    sh 'kubectl apply -f wordpress-deployment.yaml'
                    sh 'kubectl apply -f wordpress-service.yaml'
                }
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
