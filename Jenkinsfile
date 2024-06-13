pipeline {
  agent any
  stages{
    stage('build'){
      steps {
      sh 'mvn clean deploy'
      }
    }
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
