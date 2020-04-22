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
        mvn clean install -Dsonar.host.url=sonarcloud.io -Dsonar.login=4a5d8b3dc100721ac0c12cd0ad0f3abdfc7cbc35 
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
}
 
