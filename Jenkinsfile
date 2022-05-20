// Scripted Pipeline (older way of writing)
// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// }


pipeline {
	// agent { docker { image 'maven:3.6.3' } }
	agent any

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$PATH:$dockerHome/bin:$mavenHome/bin"
	}

	stages {
		stage ('Build') {
			steps {
				echo "We are in Build step"
				sh 'mvn --version'
				sh 'docker version'
				echo "Path is : $PATH"
				echo "Build Tag is : $env.BUILD_TAG"
				echo "Build Url is : $env.BUILD_URL"
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
