pipeline {
  agent any
  stages{
    stage('clone'){
      steps {
      git "https://github.com/rjraj12/hello-world/"
      }
    }
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
       bat 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.7.0.1746:sonar'
    }
    }
  }
 }
}
