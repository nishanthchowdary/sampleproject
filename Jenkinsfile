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
	  maven 'M3'
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
      steps {
      withSonarQubeEnv(credentialsId: '1234') {
    // some block
        }
        timeout(time: 10, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true
        }
      }
      }
  }
}
