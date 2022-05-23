// Scripted Pipeline (older way of writing)
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// }

// Declerative style Pipeline

pipeline {
	// agent { docker { image 'maven:3.6.3' } }
	agent any

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$PATH:$dockerHome/bin:$mavenHome/bin"
	}

	stages {
		stage ('Checkout') {
			steps {
				echo "We are in Build step"
				sh 'mvn --version'
				sh 'docker version'
				echo "Path is : $PATH"
				echo "Build Tag is : $env.BUILD_TAG"
				echo "Build Url is : $env.BUILD_URL"
			}
		}
		stage ('Compile') {
			steps {
				sh 'mvn clean compile'
			}
		}
		stage ('Test') {
			steps {
				sh 'mvn test'
			}
		}
		stage ('Integration Test') {
			steps {
				sh 'mvn failsafe:integration-test failsafe:verify'
			}
		}
		stage ('Package a JAR file') {
			steps {
				sh 'mvn package -DskipTests'
			}
		}
		stage ('Build Docker image') {
			steps {
				//"docker build -t manidonthu/currency-exchange-service:$env.BUILD_TAG"
				script {
					dockerImage = docker.build("manidonthu/currency-exchange-service:${env.BUILD_TAG}")
				}
			}
		}
		stage ('Push Docker image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}
	} 
	
// 	post {
// 		always {
// 			echo 'I run always'
// 		}
// 		success {
// 			echo 'I run when you succeed'
// 		}
// 		failure {
// 			echo 'I run when you fail'
// 		}
// 	}
}
