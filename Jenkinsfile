pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'echo "Hello world"'
        sh '''
          echo "Multiline shell steps works too"
          ls -lah
          '''
      }
    }
    stage('Deploy') {
      steps {
        retry(3) {
          sh 'echo "If I fail run me three times"'
        }
        timeout(time:3, unit: 'MINUTES') {
          sh 'echo "skip me if it takes more than 3 minutes"'
        }
      }
    }
  }
  post {
    always {
      echo 'This will always run after deploy'
    }
    success {
      echo 'This will run only if successful'
    }
    failure {
      echo 'This will run only if failed'
    }
  }
}
