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
        sh 'sudo docker build -t myalpine .'
      }
    }

    stage('Push to Dockerhub') {
      steps {
        script {
          withCredentials([usernamePassword(credentialsId: 'dockerhub-password', usernameVariable: 'DOCKERHUB_USER', passwordVariable: 'DOCKERHUB_PASSWORD')]) {
            sh 'sudo docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
            sh 'sudo docker tag myalpine:latest achanandhi/alpine-test-image:mynewimage2418'
            sh 'sudo docker push achanandhi/alpine-test-image:mynewimage2418'
          }
        }
      }
    }
  }
}
