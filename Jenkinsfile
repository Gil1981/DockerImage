pipeline {
  agent any
  stages {
    stage('Build Docker Image') {
      steps {
        git branch: 'main', url: 'https://github.com/Gil1981/Project1.git'
        sh 'docker build -t my-image .'
      }
    }
    stage('Run Unit Tests') {
      steps {
        sh 'docker run my-image npm test'
      }
      post {
        always {
          script {
            def result = currentBuild.result
            def user = env.USER
            def date = new Date().format('yyyy-MM-dd')
            def csvData = "User,Date,Test Status\n${user},${date},${result}\n"
            writeFile file: 'test-result.csv', text: csvData, encoding: 'UTF-8'
          }
        }
      }
    }
  }
}

