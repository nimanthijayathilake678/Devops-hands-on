pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t dummy-app:latest .'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
            }
        }
        stage('Push') {
            steps {
                sh 'docker tag dummy-app:latest <DOCKERHUB_USERNAME>/dummy-app:latest'
                sh 'docker push <DOCKERHUB_USERNAME>/dummy-app:latest'
            }
        }
        stage('Deploy') {
            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}
