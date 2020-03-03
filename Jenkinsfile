pipeline {
  // agent any
  agent none
  stages {
    stage('Say Hello') {
      agent { label 'nodejs-app' }
      steps {
        echo 'Hello World!'   
        sh 'java -version'
      }
    }
    stage('Test') {
      agent { label 'nodejs-app' }
      steps {
        container('nodejs') {
          echo 'Hello World from the container!'   
          sh 'java -version'
        }
      }
    }    
  }
}
