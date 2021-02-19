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
        ws(dir: 'container') {
          git(url: 'https://github.com/paloaltosoft/clearspeed_container.git', branch: 'main', changelog: true, poll: true, credentialsId: 'github')
          sh '''rm -rf clearspeed/.git
tar -cvzf clearspeed_container.tar.gz clearspeed/'''
        }

      }
    }

  }
}