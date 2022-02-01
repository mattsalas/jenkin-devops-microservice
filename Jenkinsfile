//SCRIPTED PIPELINE
// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Integration Test"
// }

//DECLARATIVE PIPELINE
pipeline {
	// agent any
	agent { docker { 
		image 'maven'
		args "-u root" 
		} }
	stages {
		stage('Build') {
			steps {
				echo "Build"
				echo "$(ps waux)"
				sh 'mvn --version'
			}
		}
		stage('Test') {
			steps {
				echo "Test"
				// sh 'pwd'
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
			}
		}
	} 
	post { 
		always {
			echo "Im awesome, I run always"
		}
		success {
			echo "I run when you are successful"
		}
		failure {
			echo "I run when you fail"
		}
	}
}
