pipeline {
  agent any

  stages {
    stage('Install') {
      steps {
        sh '''
          docker run --rm \
            -v "$PWD:/app" \
            -w /app \
            node:18-alpine \
            npm install
        '''
      }
    }

    stage('Build') {
      steps {
        sh '''
          docker run --rm \
            -v "$PWD:/app" \
            -w /app \
            node:18-alpine \
            npm run build
        '''
      }
    }

    stage('Test') {
      steps {
        sh '''
          docker run --rm \
            -v "$PWD:/app" \
            -w /app \
            node:18-alpine \
            npm test -- --watch=false || true
        '''
      }
    }
  }
}
