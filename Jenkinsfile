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
                sh 'docker build -t Test-Unit .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run Test-Unit'
            }
        }
    }

    post {
        always {
            junit 'path/to/test/results'
        }
    }
}
