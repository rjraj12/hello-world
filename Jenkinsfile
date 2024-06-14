pipeline {
  agent any
  stages{
    stage('build'){
      steps {
      bat 'mvn clean package'
      }
    }
    stage('SonarQube Analysis'){
      steps{
        script{
    def mvn = tool 'maven-tool'
      }
    withSonarQubeEnv('SonarQube'){
       bat "${mvn}/bin/sonar-scanner"
    }
    }
  }
 }
}
