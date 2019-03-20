
pipeline 
{
    agent any
    stages 
    {
        stage ('Clone') 
        {
            steps 
            {
               // git branch: 'master', url: "https://git.nagarro.com/devopscoe/training/souravraghuvanshi.git"
                
            }
        }
       
        stage ('Exec Maven') {
            steps {
                /*rtMavenRun (
                    tool: maven_3_5_4, // Tool name from Jenkins configuration
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
 