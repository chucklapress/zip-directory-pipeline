pipeline {
    agent any
    options {
        buildDiscarder(logRotator(numToKeepStr: '2', artifactNumToKeepStr: '2'))
    }
    stages {
        stage('Checkout from Git') {
            steps {
                git branch: 'main', url: 'https://github.com/chucklapress/flask_wsgi_scrap'
            }
        }
        stage ('Get Directory') {
            steps {
                    echo "$WORKSPACE"
                    sh 'mkdir archive'
                    sh 'cp -r  favicons readme.md requirements.txt templates webscraper.py  archive'
                    zip zipFile: 'archive/Repo.zip', archive: false, dir: 'archive'
                    archiveArtifacts artifacts: 'archive/*.zip', fingerprint: true
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
