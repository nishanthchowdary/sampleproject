pipeline{
 agent any
  stages{
    stage('git clone'){
     steps{
	  git 'https://github.com/nishanthchowdary/sampleproject.git'
	 }
    }
    stage('build'){
	 tools{
	  maven 'maven'
	 }
	 steps{
	 sh 'mvn clean install package'
	 }
	}
    stage('Junit'){
        steps{
          junit '**/target/surefire-reports/*.xml'
        }
    }
    stage('Sonarqube') {
    environment {
        def scannerHome = tool 'sonarQube';
    }
    steps {
      withSonarQubeEnv('sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
	      withCredentials([string(credentialsId: 'sonar', variable: 'sonarQube')]) {
    // some block
}
        }
        timeout(time: 10, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
    }
 }
}
}
