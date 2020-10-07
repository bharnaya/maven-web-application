node
{   echo "Build Number is ${env.BUILD_NUMBER}"
    def mavenHome = tool name: "maven3.6.3"
    stage('CO Checkout')  
    git branch: 'development', credentialsId: '7af012dc-0f94-4b38-9df3-c3f482536f8f', url: 'https://github.com/bharnaya/maven-web-application.git'

    stage('Build')
    {
        sh "${mavenHome}/bin/mvn clean package"
    }
    stage('SonarReport')
    {
        sh "${mavenHome}/bin/mvn sonar:sonar"
    }
     stage('Nexus Repository')
    {
        sh "${mavenHome}/bin/mvn deploy"
    }
  }
