pipeline {
    agent any
    tools {
        jdk "jdk9"
        maven "M3"
        nodejs "fosslinuxnode"
    }
 stages {
  stage ("checkout"){
           steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
  }
     stage ("Initialize") {
            steps {
                
                sh 'PATH = ${PATH}'
                    sh 'M3_HOME = ${M3_HOME}'
                
            }
        }
     stage ("Build") {
            steps {
                sh 'mvn -Dmaven.test.failure.ignore=true install' 
            }
            post {
                success {
                    junit 'target/surefire-reports/**/*.xml' 
                }
            }
         
         codesonar conditions: [cyclomaticComplexity(maxCyclomaticComplexity: 30)], credentialId: '4c856e58-e3c7-4d0a-8ebf-40dc175e7f68', hubAddress: 'https://sonarcloud.io', projectName: 'https://github.com/SAKTHISIVANI18/Coverage.git', protocol: 'http'
       
     }
    
         stage("static code analysis") {
                   steps {
                       script {
                          def scannerHome = tool 'fosslinxsonar';
                          withSonarQubeEnv("sonar") {
                          sh "${tool("fosslinxsonar")}"
                                       }
                               }
                           }
                        }
     stage("coverage"){
         steps{
     jacoco buildOverBuild: true, changeBuildStatus: true, runAlways: true, skipCopyOfSrcFiles: true
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
 

 
