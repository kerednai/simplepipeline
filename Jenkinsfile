pipeline {
  agent any
  stages {
    stage('foo') {
      steps {
        script {
          env.FILENAME = 'output.txt'
        }

        echo "${env.FILENAME}"
      }
    }
  }
}