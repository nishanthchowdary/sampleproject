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
	 sh 'mvn clean package'
	 }
	}
  }
}
