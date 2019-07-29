pipeline { 
    checkout scm
    env.WORKSPACE = pwd()
    stages {
            stage('Build from fluentd image') {
            def build_image = docker.build("fluent/fluentd:v0.12-debian", "-f Dockerfile .")
    
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
