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
		echo "Integration testing "
		sh 'mvn failsafe:integration-test failsafe:verify'
		}
	}

	stage('build jar pakaging ') {
		steps{
		echo "Pakaging  "
		sh 'mvn package'
		}
	}

	stage ('build docker image '){
		steps {
			//old way 	
			//docker build -t dnegi3000/test-jenkins-currency-conversion:$env.BUILD_TAG
		  //new 
		  script {
			 dockerImage = docker.build("dnegi3000/test-jenkins-currency-conversion:${env.BUILD_TAG}");
		  } 
		}
	}

	stage ('Push docker image '){
		steps {
			echo "Pushing image "
			//docker build -t dnegi3000/test-jenkins-currency-conversion
			script {
				docker.withRegistry('','mydockerhub'){
				dockerImage.push();
				dockerImage.push('latest');
				}
			}
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
		echo "Custom : Error "
	}
	changed {
		echo "Custom : Build status Changed  "
	}
}

}
