pipeline {
    agent any
 stages {
  stage ("checkout"){
           steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
  }
    

   stage ("sonar") {

            steps {


                    sh '/opt/apps/devops/sonar-scanner-4.2.0.1873-linux/bin/sonar-scanner'

            }

         }     
        
       stage("static code analysis") {
           steps{
    def scannerHome = tool 'sonar';
    withSonarQubeEnv('My SonarQube Server') { 
      sh "${scannerHome}/bin/sonar-scanner"
    }
           }
  }
    }
 }

 
