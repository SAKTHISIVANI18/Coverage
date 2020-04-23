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
    stage ('package') {

            steps {


                    sh './mvn clean package'

            }

         }
        
    
         stage('static code analysis') {
                   steps {
                       script {
                          def scannerHome = tool 'fosslinxsonar';
                          withSonarQubeEnv("sonar") {
                          sh "${tool("fosslinxsonar")}"
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
 

 
