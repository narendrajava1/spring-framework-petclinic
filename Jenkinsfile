@Library('jenkinssharedgroovy') _
node(label: 'master') {
    //Variables
    def gitURL='https://github.com/narendrajava1/easy-notes.git'
    def repoBranch='master'
    mvnHome = tool 'maven'
    def pom = "pom.xml"
    def goalClean = "clean compile install"
    def goalCompile = "compile"
    def goalInstall ="install"
    
    stage('Git-Checkout'){
        gitClone "${gitURL}","${repoBranch}"
        
    }
    //MVN Build stages
    stage('Maven Build and Push to Artifactory'){
       mavenBuild "${goal}"
    }
 
    stage('Maven Build and Push to Artifactory'){
       mavenBuild "${goal}"
    }
 
    stage('Maven Build and Push to Artifactory'){
       mavenBuild "${goal}"
    }
}
