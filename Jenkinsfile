pipeline {
  environment {
    registry = "dineshpsingh/todo-repo"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any

  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/dineshpsingh16/node-todo-frontend'
      }
    }
    stage('Build') {
       steps {
         sh 'npm install'
       }
    }
    stage('Test') {
      steps {
        sh 'npm test'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
         script {
            docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
