pipeline {
node {
  stage('SCM') {
    checkout scm
  }
}
  stages{
  stage('build'){
    steps {
      sh 'mvn clean deploy'
    }
   }
  stage('SonarQube Analysis') {
    def mvn = tool 'maven-tool';
    withSonarQubeEnv() {
      sh "${mvn}/bin/sonar-scanner"
    }
  }
}
}
