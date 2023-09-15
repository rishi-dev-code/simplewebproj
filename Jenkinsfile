pipeline {
  agent any
  tools {
    maven 'maven' 
  }
  stages {
    stage ('Build') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage ('Deploy') {
      steps {
        script {
          deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://172.25.251.34:8181')], contextPath: '/simplewebpipeline', onFailure: false, war: 'target/*.war' 
        }
      }
    }
  }
}