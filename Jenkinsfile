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
     stage('Unit Test Result') {
       steps {
	     junit '**/target/surefire-reports/TEST-.xml'
	   }
	}
  }
}
