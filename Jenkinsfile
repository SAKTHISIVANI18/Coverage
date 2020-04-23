pipeline {
    agent any
    tools {
        jdk "jdk9"
        maven "M3"
        nodejs "fosslinuxnode"
    }
 stages {
  stage ('checkout'){
           steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
  }
   stage ('Initialize') {
            steps {
                
                 sh 'echo "PATH = ${PATH}"'
                   sh 'echo "M3_HOME = ${M3_HOME}"'
                
            }
        }
      stage ('Build') {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
            
        }
        
    
         stage('static code analysis') {
                   steps {
                       script{
                       
                          def scannerHome = tool 'fosslinxsonar';
                          withSonarQubeEnv('sonar') {
                          sh "${scannerHome}/bin/sonar-scanner"
                          }
                                       
                               }
                           }
                        }
     stage('coverage'){
         steps{
     jacoco buildOverBuild: true, changeBuildStatus: true, runAlways: true, skipCopyOfSrcFiles: true
         }
     }

         stage('Install Dependencies') {
                                  steps {
                                        sh "npm install"

                                       }
                                }

         stage('unit Tes') {
                            steps {
                                sh "npm test"

                              }
                        }
             }
     }
 

 
