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
                    sh 'kubectl apply -f flask-deployment.yaml --validate=false'
                }
      }
    }

    stage('service') {
      steps {
        dir('ex3') {
                    sh 'kubectl apply -f flask-service.yaml --validate=false'
                }
      }
    }

  }
}
