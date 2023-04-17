pipeline {
  agent any
  environment {
    TIME = sh(script: 'date "+%Y-%m-%d %H:%M:%S"', returnStdout: true).trim()
  }
  stages {
    // stage ('checkout scm'){
    //   steps {
    //     checkout([
    //       $class: 'GitSCM',
    //       branches: [[name: 'main']],
    //       userRemoteConfigs : [[
    //         url: 'git@github.com:Gil1981/Project1',
    //         credentialsId: ''
    //       ]]
    //     ])
    //   }
    // }
    stage('Cleanup') {
      agent none
      steps {
        sh "rm -rf Project1"
      }
    }
    stage('Clone repo') {
      steps {
        sh "ls -la"
        sh "git clone https://github.com/Gil1981/Project1.git"
        sh "ls -la"
      }
    }
    stage('Build') {
      steps {
        sh "docker build -t hello-web:1 ./Project1"
        sh "docker images"
      }
    }
    stage('Run image') {
      steps {
        sh "docker run -d -p 80:80 hello-web:1"
      }
    }
  }
}

