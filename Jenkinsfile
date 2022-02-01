//SCRIPTED PIPELINE
// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Integration Test"
// }

//DECLARATIVE PIPELINE
pipeline {
	// agent any
	agent { docker { image 'maven' } }
	stages {
		stage('Build') {
			steps {
				echo "Build"
				// sh 'mvn --version'
				sh 'hostname'
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
