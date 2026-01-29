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

    stage ('Deliver') {
      steps {
        sh './jenkins/scripts/deliver.sh'
        input message: 'Finished using the web site? (Click "Proceed" to continue)' 
        sh ' /jenkins/scripts/kill.sh'
      }
    }
  }
}
