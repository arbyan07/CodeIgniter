pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'development', url: 'https://github.com/username/repo.git'
            }
        }
        stage('Install & Test') {
            steps {
                sh 'npm install'
                sh 'npm test'
            }
        }
    }
}
