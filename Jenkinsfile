pipeline {
    agent any
    stages {
        stage('create deployment') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
            }
        }

        stage('create service') {
            steps {
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}
