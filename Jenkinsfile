 pipeline {
    agent any
 stages {
  stage ("checkout"){
           steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
  }
   stage('SonarQube analysis') {
    withSonarQubeEnv(credentialsId: '4a5d8b3dc100721ac0c12cd0ad0f3abdfc7cbc35', installationName: 'sonar') { 
      sh 'mvn org.sonarsource.scanner.maven:sonar-maven-plugin:3.6.3:sonar'
    }
  }     
        
 }
 }


 
      
         
            
          
