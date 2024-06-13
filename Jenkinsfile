pipeline {
  agent any
    tools{
        maven 'maven-tool'
    }
  enviornment {
PATH = "/apache-maven-3.8.3/bin:$PATH"
  }
  stages{
    stage('build'){
      steps {
      sh 'mvn clean package'
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
