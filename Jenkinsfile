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
        sh ' sudo docker build -t myalpine .'
      }
    }

    stage('Push to Dockerhub') {
      steps {
        sh 'sudo docker login -u $DOCKERHUB_USER -p $DOCKERHUB_PASSWORD'
         // Tag the Docker image with the new repository name
         sh 'sudo docker tag myalpine:latest achanandhi/alpine-test-image:myalpine '
      // Push the Docker image to Docker Hub
       sh 'sudo docker push achanandhi/alpine-test-image:myalpine'
      }        
      }
    }

  }
  environment {
    DOCKERHUB_USER = 'achanandhi'
    DOCKERHUB_PASSWORD = 'Achanandhi@123'
  }
}
  }
}