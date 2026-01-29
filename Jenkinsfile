pipeline {
  agent {
    docker {
      image 'node:18-alpine'
      args '-u root'
    }
  }

  stages {
    stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }

    stage('Build') {
      steps {
        sh 'npm run build'
      }
    }

    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
  }
}
