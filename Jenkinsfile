pipeline {
  environment {
    registry = "ravirekha1/jenkins-slave"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }/
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/ravirekha/pipeline-project.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":latest"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '','docker-hub') {
            dockerImage.push()
          }
        }
      }
    }
  }
} 
