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
      // Note the difference between an agent and a container for steps
      agent { label 'nodejs-app' }
      steps {
        sh 'java -version'
        container('nodejs') {
          echo 'Hello World from the container!'   
          sh 'node --version'
        }
      }
    }        
    stage('Failing Stage') {
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
