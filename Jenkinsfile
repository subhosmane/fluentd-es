pipeline {
  environment {
    registry = "https://docker-registry.hostingmgmt:5000"
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/subhosmane/fluentd-es.git'
      }
    }
    stage('Building image') {
      steps {
        script {
          dockerImage = docker.build "fluentd:es"
        }
      }
    }
    stage('Deploy Image') {
      steps {
        script {
          docker.withRegistry( 'https://docker-registry.hostingmgmt:5000/' ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
