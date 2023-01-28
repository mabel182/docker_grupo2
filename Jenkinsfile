pipeline {
    environment {
    registry = "mabcontreras/https://hub.docker.com/repository/docker/mabcontreras/dockerfile_diplomado"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
    stages {
    stage('Cloning our Git') {
            steps {
            git branch: 'main', credentialsId: 'Github', url: 'https://github.com/mabel182/docker_grupo2.git'
            }
    }
  stage('Building our image') {
    steps{
    script {
      dockerImage = docker.build registry + ":$BUILD_NUMBER"
      }
    }
  }
  stage('Deploy our image') {
    steps{
      script {
        docker.withRegistry( '', registryCredential ) {
        dockerImage.push()
        }
      }
    }
  }
  }
}