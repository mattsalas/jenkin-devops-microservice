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
		stage('Checkout') {
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
		stage('Compile') {
			steps {
				echo "Compile"
				sh 'mvn clean compile'
			}
		}
		stage('Test') {
			steps {
				echo "Test"
				sh 'mvn test'
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
		stage('Package') {
			steps {
				sh 'mvn package -DskipTests'
			}
		}
		stage('Build Docker Image') {
			steps {
				// "docker build -t shamamatt/currency-exchange-devops:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("shamamatt/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerHub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
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
