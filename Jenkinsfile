pipeline {
  agent {
    docker {
      args '-p 3000:3000'
      image 'node:6-alpine'
    }
    
  }
  stages {
    stage('build') {
      environment {
        NPM_CONFIG_PREFIX = '/root/.npm'
      }
      steps {
        sh 'npm install -g'
      }
    }
  }
}