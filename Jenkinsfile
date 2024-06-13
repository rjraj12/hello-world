node {
  stage('SCM') {
    checkout scm
  }
  stage('clone-code'){
    git 'https://github.com/rjraj12/hello-world'
   }
  stage('SonarQube Analysis') {
    def mvn = tool 'maven-tool';
    withSonarQubeEnv() {
      sh "${mvn}/bin/mvn clean verify sonar:sonar"
    }
  }
}
