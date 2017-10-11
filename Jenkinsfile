node {
    
    def server = Artifactory.server "SERVER_ID"
    def rtGradle = Artifactory.newGradleBuild()
    def buildInfo

    stage('Clone sources') {
        git url: 'https://github.com/srjha/hello-ec2.git'
    }

    stage('Artifactory configuration') {
        rtGradle.tool = "gradle-4.2"
        rtGradle.deployer repo:'ext-release-local', server: server
        rtGradle.resolver repo:'remote-repos', server: server
    }

    stage('Gradle build') {
        buildInfo = rtGradle.run rootDir: "", buildFile: 'build.gradle', tasks: 'clean build'
    }

    stage('Publish build info') {
        server.publishBuildInfo buildInfo
    }
}
