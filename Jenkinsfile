@Library('jenkinssharedgroovy') _
node(label: 'master') {
    //Variables
    def gitURL='https://github.com/narendrajava1/easy-notes.git'
    def repoBranch='master'
    mvnHome = tool 'maven'
    def pom = "pom.xml"
    def goalClean = "clean"
    def goalCompile = "compile"
    def goalInstall ="install"
    
    stage('Git-Checkout'){
        gitClone "${gitURL}","${repoBranch}"
        
    }
    //MVN Build stages
    stage('Maven clean'){
       mavenBuild "${goalClean}"
    }
 
    stage('Maven compile'){
       mavenBuild "${goalCompile}"
    }
 
    stage('Maven install'){
       mavenBuild "${goalInstall}"
    }
}
