pipeline {
  agent any
  stages {
    stage('clone down') {
      steps {
        sh 'echo "Hello World"'
        stash(name: 'code', excludes: '.git')
      }
    }

    stage('say hello') {
      parallel {
        stage('say hello') {
          steps {
            sh 'echo "Hello World"'
          }
        }

        stage('build-app') {
          agent {
            docker {
              image 'gradle:jdk11'
            }

          }
          steps {
            sh 'ci/build-app.sh'
            archiveArtifacts 'app/build/libs/'
            deleteDir()
          }
        }

      }
    }

  }
}