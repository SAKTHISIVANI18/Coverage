pipeline {
    agent any
 stages {
  stage ("checkout"){
           steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
  }
    

   
        stage ("Compile") {
            steps {
                sh 'mvn clean compile'
            }
        }
        
       stage("static code analysis") {
           steps{
    def scannerHome = tool 'SonarScanner 4.3.0.2102';
    withSonarQubeEnv('My SonarQube Server') { 
      sh "${scannerHome}/bin/sonar-scanner"
    }
           }
  }
    }
 }

 
