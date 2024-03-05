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
        dir('ex3') {
                    sh 'kubectl apply -f flask-deployment.yaml'
                }
      }
    }

    stage('service') {
      steps {
        dir('ex3') {
                    sh 'kubectl apply -f flask-service.yaml'
                }
      }
    }

  }
}
