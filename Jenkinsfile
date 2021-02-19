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
          git(url: 'https://github.com/paloaltosoft/clearspeed_container.git', branch: 'main', changelog: true, poll: true, credentialsId: 'github')
          sh 'ls'
        }

      }
    }

  }
}