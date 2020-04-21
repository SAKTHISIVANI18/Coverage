 pipeline {
    agent any
 stages {
  stage ("checkout"){
           steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
  }
  stage('Sonarqube') {
    environment {
        scannerHome = tool 'sonar'
    }
    steps {
        withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
        timeout(time: 10, unit: 'MINUTES') {
            waitForQualityGate abortPipeline: true
        }
    }
}
   stage('SonarQube analysis') {
    steps{
    withSonarQubeEnv(credentialsId: '4a5d8b3dc100721ac0c12cd0ad0f3abdfc7cbc35', installationName: 'sonar') { 
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.3:sonar'
    }
    }
  }     
        
 }
 }


 
      
         
            
          
