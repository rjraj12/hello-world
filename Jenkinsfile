pipeline {
  agent {
    node {
      label 'maven'
    }
   }
  stages{
    stage('build'){
      steps {
      sh 'mvn clean deploy'
      }
    }
    stage('SonarQube Analysis'){
    def mvn = tool 'maven-tool';
    withSonarQubeEnv(){
      sh "${mvn}/bin/sonar-scanner"
    }
  }
 }
}
