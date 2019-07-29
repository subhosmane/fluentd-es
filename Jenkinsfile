pipeline { 
    checkout scm
    stages {
        stage('git url') {
            steps{
                git url: 'https://github.com/subhosmane/fluentd-es.git'
            }
        }
        stage('Build from fluentd image') {
            def build_image = docker.build("fluentd-es", "-f Dockerfile .")
            build_image.inside {
                stage('Test output') {
                    sh "ps -ef"
                }
            } 
            stage('push container image') {
                docker.withRegistry('https://docker-registry.hostingmgmt:5000') {
                    build_image.push()
                }
              }
            }
            
    }                
}
