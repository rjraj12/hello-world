pipeline {
  agent any
  stages{
    stage('SonarQube Analysis'){
      steps{
        script{
    def mvn = tool 'maven-tool'
      }
    withSonarQubeEnv('SonarQube'){
      sh "${mvn}/bin/sonar-scanner"
    }
    }
  }
 }
}
