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


                   sh 'sonar-scanner'

          }

        }     

        stage("static code analysis") {
            steps {
                withSonarQubeEnv('sonar') {
                    script {
                        def scannerHome = tool 'sonar'
                        sh "${scannerHome}/sonar"
                      sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    stage("SonarQube Quality Gate") { 
        timeout(time: 1, unit: 'HOURS') { 
           def qg = waitForQualityGate() 
           if (qg.status != 'OK') {
             error "Pipeline aborted due to quality gate failure: ${qg.status}"
           }
        }
    }
 }
 }
}

 
      
         
            
          
