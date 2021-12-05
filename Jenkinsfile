pipeline {
  agent any
  stages {
    stage('Build&Test') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore clean package'
        stash(name: 'build-test-artifacts', includes: '**/target/surefie-reports/TEST-*,xml.target/*.jar')
      }
    }

  }
}