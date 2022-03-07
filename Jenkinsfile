pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '2'))
    }
    stages {
        stage('Checkout from Git') {
            steps {
                git branch: 'master', url: 'https://github.com/chucklapress/portfolio'
            }
        }
        stage ('Get Directory') {
            steps {
              zip zipFile: 'repo.zip', archive: true, exclude: 'db.sqlite3, README.md'
              // first argument is zipfile name, second argument leave artifact on server
              // third argument is list of files to exclude from zip package
            }
          }
        }
        post {
          always {
            script {
              deleteDir()
            }
          }
        }
      }
