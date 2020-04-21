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
    withSonarQubeEnv(credentialsId: '74437adc-a28c-49ea-9cf6-6fce2acf95fe', installationName: 'sonar') { 
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.3:sonar'
    }
    }
  }     
        
 }
 }


 
      
         
            
          
