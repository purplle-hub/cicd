pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'make'
        archiveArtifacts(artifacts: '/var/www/html/', fingerprint: true)
      }
    }
    stage('Test') {
      steps {
        sh 'make check || true'
        junit '/var/www/html/*.xml'
      }
    }
    stage('Deploy') {
      when {
        expression {
          currentBuild.result == null || currentBuild.result == 'SUCCESS'
        }

      }
      steps {
        sh 'make publish'
      }
    }
  }
}