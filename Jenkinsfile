pipeline {
    agent any
 stages {
  stage ("checkout"){
           steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
  }
    

   
        stage ('Compile') {
            steps {
                sh 'mvn clean compile -DskipTests -U -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true'
            }
        }
        
        stage ('SonarQube') {
            steps {
                script {
                    if (env.GIT_BRANCH == 'master') {
                        withSonarQubeEnv ('SonarQube') {
                            sh 'mvn package -DskipTests -U sonar:sonar -Dsonar.branch.name=master -Dsonar.host.url=SONARQUBE_SERVER_URL -Dsonar.login=18b145db92099cd1ae7fc5514633ccf07ada9243 -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true'
                        }
                    } else if (env.GIT_BRANCH == 'development') {
                        withSonarQubeEnv ('SonarQube') {
                            sh 'mvn package -DskipTests -U sonar:sonar -Dsonar.branch.name=development -Dsonar.host.url=SONARQUBE_SERVER_URL -Dsonar.login=18b145db92099cd1ae7fc5514633ccf07ada9243 -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true'
                        }
                    } else {
                        withSonarQubeEnv ('SonarQube') {
                            sh 'mvn package -DskipTests -U sonar:sonar -Dsonar.branch.name=refs/pull-requests/${PRID}/from -Dsonar.host.url=SONARQUBE_SERVER_URL -Dsonar.login=18b145db92099cd1ae7fc5514633ccf07ada9243 -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true -Dmaven.wagon.http.ssl.ignore.validity.dates=true'
                        }
                    }
                }
            }
        }
    }
 }

 
