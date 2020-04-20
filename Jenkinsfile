pipeline {
    agent any
    tools {
        jdk 'jdk10'
        maven 'M3'
    }

    environment {
        JAVA_HOME = "${jdk}"
    }

    stages {
        stage('checkout') {
            steps {
                git https://github.com/SAKTHISIVANI18/Coverage.git
            }
        }

        stage('Test') {
            steps {
                sh 'mvn install'
            }
        }

        stage('static code analysis') {
            steps {
                withSonarQubeEnv('sonar') {
                    script {
                        def scannerHome = tool 'sonarqube-scanner'
                        sh "${scannerHome}/bin/sonar-scanner"
                    }
                }
            }
        }
    }
}
