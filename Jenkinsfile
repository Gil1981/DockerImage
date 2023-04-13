pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Gil1981/DockerImage'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t DockerImage .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run DockerImage npm test'
            }
        }
    }

    post {
        always {
            junit 'path/to/test/results'
        }
    }
}
