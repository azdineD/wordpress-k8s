pipeline {
  agent any

  environment {
    IMAGE = "lina2015/wordpress-k8s"
    TAG = "v1"
  }

  stages {
    stage('Build Docker Image') {
      steps {
        sh 'docker build -t $IMAGE:$TAG .'
      }
    }

    stage('Push to Docker Hub') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
          sh 'echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin'
          sh 'docker push $IMAGE:$TAG'
        }
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        sh 'kubectl apply -f k8s/deployment.yml'
        sh 'kubectl apply -f k8s/service.yml'
      }
    }
  }
}
