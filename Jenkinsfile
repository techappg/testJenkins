pipeline {
  agent any
  stages {
    stage('check version') {
      steps {
        sh 'git --version'
      }
    }

    stage('build') {
      steps {
        dir(path: 'container') {
          sh 'ls'
        }

      }
    }

  }
}