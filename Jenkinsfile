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
        timeout(time: 1, unit: 'HOURS') { 
           def qg = waitForQualityGate() 
           if (qg.status != 'OK') {
             error "Pipeline aborted due to quality gate failure: ${qg.status}"
           }
        }
    }
    }
 }

 
