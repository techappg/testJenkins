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
            sh 'mkdir -p execution-service'
            dir(path: 'execution-service') {
              git(url: 'https://github.com/techappg/execution-service-arch.git', branch: 'main', credentialsId: 'github')
            }

            stash(name: 'execution-service', excludes: '.git')
          }
        }

        stage('Participant service') {
          steps {
            echo 'participant service'
            sh 'mkdir -p participant-service'
            dir(path: 'participant-service') {
              git(url: 'https://github.com/techappg/participant-service-arch.git', branch: 'main', credentialsId: 'github')
            }

            stash(name: 'participant-service', excludes: '.git')
          }
        }

        stage('Project service') {
          steps {
            echo 'project service'
            sh 'mkdir -p project-service'
            dir(path: 'project-service') {
              git(url: 'https://github.com/techappg/project-service-arch.git', branch: 'main', credentialsId: 'github')
            }

            stash(name: 'project-service', excludes: '.git')
          }
        }

        stage('User service') {
          steps {
            echo 'user service'
            sh 'mkdir -p user-service'
            dir(path: 'user-service') {
              git(url: 'https://github.com/techappg/user-service-arch.git', branch: 'main', credentialsId: 'github')
            }

            stash(name: 'user-service', excludes: '.git')
          }
        }

        stage('Webapp') {
          steps {
            echo 'webapp'
            sh 'mkdir -p node'
            dir(path: 'node') {
              git(url: 'https://github.com/techappg/webapp-arch.git', branch: 'main', credentialsId: 'github')
            }

            stash(name: 'node', excludes: '.git')
          }
        }

      }
    }

    stage('Configure Environment') {
      steps {
        echo 'configure docker environment'
        git(url: 'https://github.com/techappg/base-arch.git', branch: 'main', credentialsId: 'github')
        unstash 'auth-service'
        unstash 'execution-service'
        unstash 'participant-service'
        unstash 'project-service'
        unstash 'user-service'
        unstash 'node'
      }
    }

    stage('Finish') {
      steps {
        echo 'Finished'
      }
    }

  }
}
