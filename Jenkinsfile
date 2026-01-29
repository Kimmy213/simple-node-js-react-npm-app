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

    
    }
  }
}
