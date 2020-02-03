@Library('jenkinssharedgroovy') _
node(label: 'master') {
    //Variables
    def gitURL='https://github.com/narendrajava1/spring-framework-petclinic.git'
    def repoBranch='master'
    mvnHome = tool 'maven'
    def pom = "pom.xml"
    def goalClean = "clean"
    def goalCompile = "compile"
    def goalInstall ="install"
    def scannerHome = tool 'SonarQubeScanner'    
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
    
    stage('Sonarqube') {
         withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
             timeout(time: 1, unit: 'MINUTES') { 
            def qg = waitForQualityGate() 
           if (qg.status != 'OK') {
           error "Pipeline aborted due to quality gate failure: ${qg.status}"
           currentBuild.status='FAILURE'
      }
    }
        }
        
    
}
}
