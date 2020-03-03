pipeline {
  // agent any
  agent none
  options {
    buildDiscarder(logRotator(numToKeepStr: '20'))
    skipDefaultCheckout true
  }
  stages {
    stage('Test') {
      agent { label 'nodejs-app' }
      steps {
        checkout scm
        container('nodejs') {
          echo 'Hello World show checkout!'   
          sh 'node --version'
        }
      }
    }     
    stage('Say Hello') {
      agent { label 'nodejs-app' }
      steps {
        echo 'Hello World!'   
        sh 'java -version'
      }
    }
    stage('Show difference between agent and container') {
      // Note the difference between an agent and a container for steps
      agent { label 'nodejs-app' }
      steps {
        sh 'java -version'
        container('nodejs') {
          echo 'Hello World from the container with node installed!'   
          sh 'node --version'
        }
      }
    }        
    stage('Failing Stage') {
      agent { label 'nodejs-app' }
      steps {
        container('nodejs') {
          echo 'Hello World from the container without java!'   
          sh 'java -version'
        }
      }
    }    
  }
}
