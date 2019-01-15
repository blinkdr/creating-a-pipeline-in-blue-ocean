pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000'
    }

  }
  stages {
    stage('install ') {
      steps {
        sh 'npm install '
      }
    }
    stage('build') {
      steps {
        sh 'npm build'
      }
    }
    stage('test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
  }
}