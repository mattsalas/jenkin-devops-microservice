//SCRIPTED PIPELINE
// node {
// 	echo "Build"
// 	echo "Test"
// 	echo "Integration Test"
// }

//DECLARATIVE PIPELINE
// pipeline {
// 	// agent any
// 	agent { docker { image 'maven' } }
// 	stages {
// 		stage('Build') {
// 			steps {
// 				echo "Build"
// 				// echo "${pwd}"
// 				// sh 'mvn --version'
// 				sh "whoami"
// 			}
// 		}
// 		stage('Test') {
// 			steps {
// 				echo "Test"
// 				// sh 'pwd'
// 			}
// 		}
// 		stage('Integration Test') {
// 			steps {
// 				echo "Integration Test"
// 			}
// 		}
// 	} 
// 	post { 
// 		always {
// 			echo "Im awesome, I run always"
// 		}
// 		success {
// 			echo "I run when you are successful"
// 		}
// 		failure {
// 			echo "I run when you fail"
// 		}
// 	}
// }

pipeline {
    agent none
    stages {
        stage('Test') {
            agent {
                docker {
                    image 'maven'
                    alwaysPull true
                }
            }
            steps {
                sh 'pwd'
                sh 'mvn --version'
            }
        }
    }
}
