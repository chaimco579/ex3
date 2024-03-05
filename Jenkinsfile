pipeline {
  agent any
  stages {
    stage('k8s') {
      steps {
        sh 'echo starting k8s'
      }
    }

    stage('deployment') {
      steps {
        sh 'kubectl apply -f /home/pini/k8s/flask-deployment.yaml --validate=false'
      }
    }

    stage('service') {
      steps {
        sh 'kubectl apply -f /home/pini/k8s/flask-service.yaml --validate=false'
      }
    }

  }
}
