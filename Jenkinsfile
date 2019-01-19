node {
    env.JAVA_HOME="${tool 'Java'}"
    env.PATH="${env.JAVA_HOME}/bin:${env.PATH}"
    sh 'java -version'
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/dineshp4/crudApp.git'
      // Get the Maven tool.
      // ** NOTE: This 'M3' Maven tool must be configured
      // **       in the global configuration.           
      mvnHome = tool 'Maven'
   }
   stage('Build') {
       // Run the maven build
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean package"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   agent { dockerfile true }
   stage('Test') {
        steps {
            sh 'java -version'
        }
   }
    
//   stage('Results') {
//      junit '**/target/surefire-reports/TEST-*.xml'
//      archive 'target/*.jar'
//   }
}
