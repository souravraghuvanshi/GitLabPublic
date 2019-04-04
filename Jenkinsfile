node {
    
    def server = Artifactory.server 'artifactory'
    def rtMaven = Artifactory.newMavenBuild()
    def buildInfo
    def mvnHome
    stage ('Clone') {
        git url: 'https://github.com/souravraghuvanshi/GitLabPublic.git'
    }

    stage ('Artifactory configuration') {
        mvnHome = tool 'Maven_Home'
        rtMaven.tool = 'Maven_Home' // Tool name from Jenkins configuration
        rtMaven.deployer releaseRepo: 'libs-release-local', snapshotRepo: 'libs-snapshot-local', server: server
        rtMaven.resolver releaseRepo: 'libs-release', snapshotRepo: 'libs-snapshot', server: server
        buildInfo = Artifactory.newBuildInfo()
        buildInfo.env.capture = true
    }

    stage ('Exec Maven') {
        rtMaven.run pom: 'pom.xml', goals: 'clean install', buildInfo: buildInfo
    }

    stage ('Publish build info') {
        server.publishBuildInfo buildInfo
    }
}
