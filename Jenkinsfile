pipeline {
  agent any
  stages {
    stage('Build result') {
      steps {
        sh 'sudo docker build -t dockersamples/result ./result'
      }
    } 
    stage('Build vote') {
      steps {
        sh 'sudo docker build -t dockersamples/vote ./vote'
      }
    }
    stage('Build worker') {
      steps {
        sh 'sudo docker build -t dockersamples/worker ./worker'
      }
    }
    stage('Push result image') {
         steps {
       withDockerRegistry(credentialsId: 'login', url: 'https://index.docker.io/') {
          sh 'sudo docker push dockersamples/result'
       } 
      }
    }
    stage('Push vote image') {
         steps {
       withDockerRegistry(credentialsId: 'login', url: 'https://index.docker.io/') {
          sh 'sudo docker push dockersamples/vote'
       } 
      }
    }
    stage('Push worker image') {
         steps {
            withDockerRegistry(credentialsId: 'login', url: 'https://index.docker.io/') {
          sh 'sudo docker push dockersamples/worker'
            }
        }      }
    }
  }


