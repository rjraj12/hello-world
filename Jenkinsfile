pipeline {
  agent none
  stages{
    stage('build'){
      steps {
      sh 'mvn clean deploy'
      }
    }
    stage('SonarQube Analysis'){
    def mvn = tool 'maven-tool'
    steps {
    withSonarQubeEnv('My SonarQube Server'){
      sh "${mvn}/bin/sonar-scanner"
    }
    }
  }
 }
}
