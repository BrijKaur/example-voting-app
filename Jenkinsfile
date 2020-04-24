pipeline {
  agent any
  stages {
    stage('Build result') {
      steps {
        sh 'sudo docker build -t brijkaur/votingresult ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'sudo docker build -t brijkaur/votingvote ./vote'
      }
    }
    stage('Build worker') {
      steps {
        sh 'sudo docker build -t brijkaur/votingworker ./worker'
      }
    }
    stage('Push result image') {
         steps {
       withDockerRegistry(credentialsId: 'login', url: 'https://index.docker.io/') {
          sh 'sudo docker push brijkaur/votingresult'
       } 
      }
    }
    stage('Push vote image') {
         steps {
       withDockerRegistry(credentialsId: 'login', url: 'https://index.docker.io/') {
          sh 'sudo docker push brijkaur/votingvote'
       } 
      }
    }
    stage('Push worker image') {
         steps {
            withDockerRegistry(credentialsId: 'login', url: 'https://index.docker.io/') {
          sh 'sudo docker push brijkaur/votingworker'
            }
        }      }
    }
  }


