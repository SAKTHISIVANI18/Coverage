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
          steps{
        timeout(time: 1, unit: 'HOURS') { 
            withSonarQubEnv('sonar'){
                script{
                    def scannerHome = tool 'sonar'
                    sh "${scannerHome}/bin/sonar-scanner"
        }
        }
    }
    }
 }
 }
}

 
