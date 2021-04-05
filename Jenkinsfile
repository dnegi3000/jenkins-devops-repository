//Delrative
pipeline {
	//agent {docker {image 'maven:3.6.3'}} 
	agent any 
	environment {
		mavenHome = tool 'mymaven'
		dockerHome = tool 'mydocker'
		PATH ="$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages {	
	stage('Build') {
		steps{
			echo "Building ....."
			sh 'mvn --version'
		
		}
	}

	stage('compile') {
		steps{
			echo "Building ....."
			sh 'mvn clean compile'
		
		}
	}

	stage('test') {
		steps{
		echo "testing "
		sh 'mvn test'
		}
	}
	stage('Integratin test') {
		steps{
		echo "Integratin testing "
		sh 'failsafe:integration-test failsafe:verify'
		}
	}
}
post {

	always {
		echo "Custom :Build finishd."
	}
	success {
		echo "Custom :Success"

	}
	failure {
		chho "Custom : Error "
	}
	changed {
		chho "Custom : Build status Changed  "
	}
}

}
