pipeline {
  environment {
    registry = "https://docker-registry.hostingmgmt:5000/fluentd"
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
          dockerImage = docker.build .
        }
      }
    }
    stage('Deploy Image') {
      steps {
        script {
          docker.withRegistry( '' ) {
            dockerImage.push()
          }
        }
      }
    }
  }
}
