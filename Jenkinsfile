pipeline {
  agent any
  stages {
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