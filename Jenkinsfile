pipeline {
    agent any
    tools {nodejs "fosslinuxnode"}
 stages {
  stage ("checkout"){
           steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
  }
    
         stage("static code analysis") {
                   steps {
                       script {
                          def scannerHome = tool 'fosslinxsonar';
                          withSonarQubeEnv("sonar") {
                          sh "${tool("fosslinxsonar")}/bin/sonar-scanner"
                                       }
                               }
                           }
                        }

         stage("Install Dependencies") {
                                  steps {
                                        sh "npm install"

                                       }
                                }

         stage("unit Test") {
                            steps {
                                sh "npm test"

                              }
                        }
             }
     }
 

 
