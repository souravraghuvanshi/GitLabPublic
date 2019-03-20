 
pipeline 
{
    agent any
    stages 
    {
       
        stage ('Exec Maven') {
            steps {
                /*rtMavenRun (
                    tool: Maven_Home, // Tool name from Jenkins configuration
                    pom: 'maven-example/pom.xml',
                    goals: 'clean install',
                    deployerId: "MAVEN_DEPLOYER",
                    resolverId: "MAVEN_RESOLVER"
                )*/
                
                sh 'mvn clean install'
            }
        }
           stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
    }
} 
 
