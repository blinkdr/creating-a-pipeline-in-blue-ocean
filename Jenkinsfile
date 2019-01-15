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
        sh 'npm install --registry=https://registry.npm.taobao.org'
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
    stage('deploy') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input ' Finished using the web site? (Click "Proceed" to continue'
        sh './jenkins/scripts/kill.sh'
      }
    }
  }
}