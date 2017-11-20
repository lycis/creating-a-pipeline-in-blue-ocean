pipeline {
  agent {
    docker {
      image 'node:6-alpine'
      args '-p 3000:3000 -u root'
    }
    
  }
  stages {
    stage('build') {
      environment {
        NPM_CONFIG_PREFIX = '/root/.npm'
      }
      steps {
        sh 'mkdir /.npm'
        sh 'npm install'
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
    stage('deliver') {
      steps {
        sh './jenkins/scripts/deliver.ah'
        input 'Finished using the web site? (Click "Proceed" to continue)'
      }
    }
  }
}