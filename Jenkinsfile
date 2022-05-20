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
	agent any
	stages {
		stage ('Build') {
			steps {
				echo "Build"
			}
		}
		stage ('Test') {
			steps {
				echo "Test"
			}
		}

	} 
	
	post {
		always {
			echo 'I run always'
		}
		success {
			echo 'I run when you succeed'
		}
		failue {
			echo 'I run when you fail'
		}
	}
}
