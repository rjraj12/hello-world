def registry = "https://rajeev23.jfrog.io/"
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
    stage('War Publish') {
      steps {
        script {
          echo '<----------------- war file publishing starts ---------------------->'
          echo '<---- ${registry} ------>'
           def server = Artifactory.newServer url:registry+"/artifactory", credentialsId: 'jfrog'
           def properties = "buildid=${env.BUILD_ID},commitid=${GIT_COMMIT}";
           def uploadSpec = """{
               "files": [
                 {
                   "pattern": "webapp/*",
                   "target": "mavtest-libs-release-local/",
                   "flat": "false",
                   "props": "${properties}",
                   "exclusions": ["*.sha1", "*.md5"]
                }
            ]
          }"""
          def buildInfo = server.upload(uploadSpec)
          buildInfo.env.collect()
          server.publishBuildInfo(buildInfo)
          echo '<-------------- war publish ------------>'
        }
    }
   }
 }
}
