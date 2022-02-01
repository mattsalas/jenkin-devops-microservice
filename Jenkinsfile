//SCRIPTED PIPELINE
// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Integration Test"
// }

//DECLARATIVE PIPELINE
pipeline {
	agent any
	// agent { docker { image 'maven' } }

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$mavenHome/bin:$dockerHome/bin:$PATH"
	}

	stages {
		stage('Build') {
			steps {
				echo "Build"
				sh 'mvn --version'
				// sh 'hostname'
				sh 'docker version'
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
				echo "JOB_NAME - $env.JOB_NAME"

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
