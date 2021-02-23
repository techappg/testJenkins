pipeline {
  agent any
  stages {
    stage('Build service') {
      parallel {
        stage('Auth service') {
          steps {
            echo 'auth service'
            sh 'mkdir -p auth-service'
            dir(path: 'auth-service') {
              git(url: 'https://github.com/techappg/auth-service-arch.git', branch: 'main', credentialsId: 'github')
            }

            stash(name: 'auth-service', excludes: '.git')
          }
        }

        stage('Execution service') {
          steps {
            echo 'execution service'
          }
        }

        stage('Participant service') {
          steps {
            echo 'participant service'
          }
        }

        stage('Project service') {
          steps {
            echo 'project service'
          }
        }

        stage('User service') {
          steps {
            echo 'user service'
          }
        }

        stage('Webapp') {
          steps {
            echo 'webapp'
          }
        }

      }
    }

    stage('Configure Environment') {
      steps {
        echo 'configure docker environment'
        git(url: 'https://github.com/techappg/base-arch.git', branch: 'main', credentialsId: 'github')
        unstash 'auth-service'
      }
    }

    stage('Finish') {
      steps {
        echo 'Finished'
      }
    }

  }
}