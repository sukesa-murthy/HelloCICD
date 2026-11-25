pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps { checkout scm }
        }
        stage('Build') {
            steps { bat 'mvn clean compile' }
        }
        stage('Test') {
            steps { bat 'mvn test' }
        }
        stage('Package') {
            steps { bat 'mvn package' }
        }
        stage('Docker Build') {
            steps { bat 'docker build -t hellocicd .' }
        }
        stage('Deploy') {
            steps {
                bat 'docker rm -f mycicdapp || exit /b 0'
                bat 'docker run --name mycicdapp hellocicd'
            }
        }
    }
}
