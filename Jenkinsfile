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

    stage('static analysis') {
      steps {
        sh '''./mvnw clean verify -DskipTests=true  sonar:sonar \\
  -Dsonar.projectKey=nsp-aw8-petclinic \\
  -Dsonar.host.url=http://13.233.135.239:9000 \\
  -Dsonar.login=sqp_ef894d674151267480446ec4976246f858f627c1'''
      }
    }

    stage('unit test') {
      steps {
        sh './mvnw "-Dtest=**/petclinic/*/*.java" test'
      }
    }

    stage('package') {
      steps {
        sh './mvnw package -DskipTests=true'
      }
    }

    stage('deploy') {
      steps {
        sh './mvnw spring-boot:run </dev/null &>/dev/null &'
      }
    }

  }
}