pipeline {
    agent any

    stages {
        stage('login') {
            steps {
                sh 'docker login -u marcorezkallah -p ${DOCKERHUB_PASSWORD}'
            }
        }


        stage('docker build local image') {
            steps {
                sh 'docker build . -t marcorezkallah/nti-cicd-project:v1.0'
            }
        }

        stage('docker push local image') {
            steps {
                sh 'docker push marcorezkallah/nti-cicd-project:v1.0'
            }
        }

        stage('Cleaning up') {
            steps {
                sh "docker rmi marcorezkallah/nti-cicd-project:v1.0"
            }
        }

    }
}
