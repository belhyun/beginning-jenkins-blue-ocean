pipeline {
  agent {
    node {
      label 'docker'
    }

  }
  stages {
    stage('Build&Test') {
      steps {
        sh 'mvn -Dmaven.test.failure.ignore clean package'
        stash(name: 'build-test-artifacts', includes: '**/target/surefie-reports/TEST-*,xml.target/*.jar')
      }
    }

    stage('Report & Publish') {
      steps {
        unstash 'build-test-artifacts'
        junit '**/target/surefire-reports/TEST-*.xml'
        archiveArtifacts 'target/*.jar'
      }
    }

  }
  environment {
    branch = 'feature/ch03'
  }
}