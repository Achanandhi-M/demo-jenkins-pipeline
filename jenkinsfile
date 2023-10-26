pipeline {
  agent any
  stages {
    stage('Check out code') {
      steps {
        git(url: 'https://github.com/Achanandhi-M/demo-jenkins-pipeline.git', branch: 'main')
      }
    }


    stage('Build') {
      steps {
        sh ' sudo docker build -t myimage .'
      }
    }

    stage('Push to Dockerhub') {
      steps {
        sh 'sudo docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
      }
    }

  }
}