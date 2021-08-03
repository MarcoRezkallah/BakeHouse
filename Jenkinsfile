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
                sh 'docker build . -t marcorezkallah/nti-cicd-project:v1.$BUILD_NUMBER'
            }
        }

        stage('docker push local image') {
            steps {
                sh 'docker push marcorezkallah/nti-cicd-project:v1.$BUILD_NUMBER'
            }
        }

        stage('docker tag latest') {
            steps {
                sh 'docker image tag marcorezkallah/nti-cicd-project:v1.$BUILD_NUMBER marcorezkallah/nti-cicd-project:latest'
            }
        }

        stage('push latest') {
            steps {
                sh 'docker push marcorezkallah/nti-cicd-project:latest'
            }
        }

        stage('Cleaning up') {
            steps {
                sh 'docker rmi marcorezkallah/nti-cicd-project:v1.$BUILD_NUMBER'
                sh 'docker rmi marcorezkallah/nti-cicd-project:latest'
            }
        }
    }
}
