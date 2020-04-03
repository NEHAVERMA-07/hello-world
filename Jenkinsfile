
node {
   def mvnHome
   stage('Git Checkout') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/mkyong/spring3-mvc-maven-xml-hello-world.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool name: 'M3', type: 'maven'
   }
   stage('Build') {
      // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
      echo 'this is build maven artifact'
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
    stage('artifact') {
      
      archiveArtifacts 'target/*.war'
   }
stage ('deploy'){
   echo 'deployment started'
       deploy adapters: [tomcat8(credentialsId: '9098c965-68b5-49a5-a0fe-f3650c5ce5f2', path: '', url: 'http://35.239.183.128:8090/')], contextPath: null, war: '**/*.war'
   }
}
