pipeline {
  agent any
  stages {
    stage('k8s') {
      steps {
        deleteDir()
        sh 'echo starting k8s'
        sh 'git clone https://github.com/chaimco579/ex3.git' 
      }
    }

    stage('deployment') {
      steps {
        dir('ex3') {
                    sh 'cat flask-deployment.yaml'
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
