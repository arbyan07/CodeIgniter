pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Contoh build command, misal:
                sh 'docker build -t myapp:${GIT_COMMIT} .'
            }
        }
        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'pytest tests/' // contoh menjalankan tes python
            }
        }
        stage('Deploy to Kubernetes') {
            when {
                expression {
                    // Deploy hanya jika stage Test berhasil
                    currentBuild.currentResult == 'SUCCESS'
                }
            }
            steps {
                echo 'Deploying to Kubernetes staging...'

                // Login ke cluster Kubernetes (pastikan kubeconfig sudah disiapkan)
                sh '''
                kubectl config use-context my-staging-cluster-context
                kubectl set image deployment/myapp-deployment myapp=myregistry/myapp:${GIT_COMMIT} -n staging
                kubectl rollout status deployment/myapp-deployment -n staging
                '''
            }
        }
    }
}
