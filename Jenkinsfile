pipeline {
  agent {
    node {
      label 'nsp-aw8-node2'
    }

  }
  stages {
    stage('compile') {
      steps {
        sh './mvnw clean compile'
        echo 'Jenkins start'
      }
    }

  }
}