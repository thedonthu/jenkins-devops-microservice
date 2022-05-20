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
	agent { docker { image 'maven:3.6.3' } }
	stages {
		stage ('Build') {
			steps {
				sh 'mvn --version'
				echo "Build"
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
