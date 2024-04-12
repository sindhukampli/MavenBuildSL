pipeline {
	agent any
	
	stages{
		stage('Checkout Code'){
			steps{
				checkout scm
				}
			}
	
	stage('Build'){
		steps{
			bat "mvn clean install -Dmaven.test.skip=true"
		}
	}
	
	stage('Archive Artifact'){
		steps{
		archiveArtifacts artifacts:'target/*.war'
		}
	}
	
	stage('deployment'){
		steps{
		deploy adapters: [tomcat9(url: 'http://13.127.42.108:8080/', 
                              credentialsId: 'TomcatCreds')], 
                     war: 'target/*.war',
                     contextPath: 'app'
		}
		
	}
	

	}
}
