pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/your-repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t your-image-name .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run your-image-name npm test'
            }
        }
    }

    post {
        always {
            junit 'path/to/test/results'
        }
    }
}
