pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'development', url: 'https://github.com/arbyan07/CodeIgniter'
            }
        }

        stage('Build') {
            steps {
                echo 'No build needed for PHP project'
            }
        }

        stage('Test') {
            steps {
                echo 'Add PHP unit tests here if needed'
            }
        }
    }
}
