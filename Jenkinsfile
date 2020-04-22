pipeline {
    agent any
 stages {
  stage ("checkout"){
           steps {
                git 'https://github.com/SAKTHISIVANI18/Coverage.git'
            }
  }
 
    stage("Statical Code Analysis") {
        steps{
       
    withSonarQubeEnv('sonarcloud.io') {
        mvn ‘${SONAR_MAVEN_GOAL} -Dsonar.host.url=${SONAR_HOST_URL} -Dsonar.login=${SONAR_AUTH_TOKEN} ${SONAR_EXTRA_PROPS} ‘
    }
    timeout(time: 2, unit: 'MINUTES') {
        def qg = waitForQualityGate()
        if (qg.status != 'OK') {
            currentBuild.result = 'UNSTABLE'
        }  
        
    }
}

}
 }
 
