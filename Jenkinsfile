pipeline {  
       agent any
       tools {
              maven 'maven'
       }
    stages {       
        stage('Cleanup Workspace') {
            steps {
               sh 'mvn clean'
            }
        }
        stage('Code test') {
            steps {
              sh 'mvn test'
            }
        }
        stage('Code Build') {
            steps {
             sh 'mvn package'
            }
        } 
        stage ('Deploy') {
            steps {
              script {
                      deploy adapters: [tomcat9(credentialsId: 'tomcat_credential', path: '', url: 'http://192.168.133.128:8081')], contextPath: '/gosecuri', onFailure: false, war: 'target/*.war' 
        }
      }
    }
    } 
}
