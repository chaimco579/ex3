pipeline {
    agent any
    stages {
        stage('k8s') {
            steps {
                deleteDir()
                sh 'echo starting k8s...'
                sh 'echo cloning project...'
                sh 'git clone https://github.com/chaimco579/ex3.git'
            }
        }

        stage('deployment') {
            steps {
                dir('ex3') {
                    script {
                        def deploymentExists = sh(script: 'kubectl get deployment flask2-deployment -o name', returnStatus: true)
                        if (deploymentExists == 0) {
                            echo 'Deleting existing deployment...'
                            sh 'kubectl delete deployment flask2-deployment'
                        }

                        echo 'Applying deployment...'
                        sh 'kubectl apply -f flask-deployment.yaml'
                    }
                }
            }
        }

        stage('service') {
            steps {
                dir('ex3') {
                    script {
                        def serviceExists = sh(script: 'kubectl get service flask2-service -o name', returnStatus: true)
                        if (serviceExists == 0) {
                            echo 'Deleting existing service...'
                            sh 'kubectl delete service flask2-service'
                        }

                        echo 'Applying service...'
                        sh 'kubectl apply -f flask-service.yaml'
                    }
                }
            }
        }
    }
}
