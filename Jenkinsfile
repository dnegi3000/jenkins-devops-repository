//Delrative
pipeline {
	agent {docker {image 'maven:3.6.3'}} 
	stages {	
	stage('Build') {
		steps{
			echo "Building ....."
			sh 'mvn --version'
		
		}
	}
	stage('test') {
		steps{
		echo "test"
		}
	}
	stage('Integratin test') {
		steps{
		echo "Integratin test"
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
