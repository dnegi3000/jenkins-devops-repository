//Delrative
pipeline {
	agent any 
	stages {
	stage('Build') {
		steps{
		echo "Build"
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
} post {

	always {
		echo "Build finishd."
	}
	success {
		echo "Success"

	}
	failure {
		chho "Error "
	}
}

}
