pipeline {
    agent any

    stages {
        stage('Cloner le dépôt') {
            steps {
                git 'https://github.com/azdineD/wordpress-k8s.git'
            }
        }

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
