pipeline {
   agent any

   stages {
      stage('Build') {
         steps {
            git 'https://github.com/jglick/simple-maven-project-with-tests.git'
            sh 'mvn clean compile'
         }
      }
      
      stage('Test') {
         steps {
            sh 'mvn clean test'
         }
      }
      
      stage('Deploy') {
         steps {
            sh 'mvn deploy -DaltDeploymentRepository=nexus::default::http://localhost:8081/nexus/content/repositories/releases'
         }
         post {
            success {
               archiveArtifacts 'target/*.jar'
            }
         }
      }
   }
}
