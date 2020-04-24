pipeline {
  agent any
  stages {
    stage('Build result') {
      steps {
        sh 'sudo docker build -t brijkaur/votingresult:v1 ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'sudo docker build -t brijkaur/votingvote:v1 ./vote'
      }
    }
    stage('Build worker') {
      steps {
        sh 'sudo docker build -t brijkaur/votingworker:v1 ./worker'
      }
    }
    stage('Push result image') {
         steps {
       withDockerRegistry(credentialsId: 'login', url: "https://https://registry.hub.docker.com/") {
          sh 'sudo docker push brijkaur/votingresult:v1'
       } 
      }
    }
    stage('Push vote image') {
         steps {
       withDockerRegistry(credentialsId: 'login', url: "") {
          sh 'sudo docker push brijkaur/votingvote:v1'
       } 
      }
    }
    stage('Push worker image') {
         steps {
            withDockerRegistry(credentialsId: 'login', url: 'https://index.docker.io/') {
          sh 'sudo docker push brijkaur/votingworker:v1'
            }
        }      }
    }
  }


