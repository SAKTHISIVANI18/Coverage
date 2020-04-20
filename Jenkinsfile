pipeline {
    agent any
    tools {
        jdk 'jdk13.0.1'
        maven 'M3'
    }

    environment {
        JAVA_HOME = "${jdk}"
    }

    stages {
        stage('checkout') {
            steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn install'
            }
        }
        stage ('sonar') {

          steps {


                   sh 'sonar-scanner'

          }

        }     

        stage('static code analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    script {
                        def scannerHome = tool 'Sonar'
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }
}
