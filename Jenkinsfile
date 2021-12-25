pipeline {
	agent any
	stages{
		stage('Build') {
			steps {
				echo "Build"
			}
		}
		stage('test') {
			steps {
				echo "test"
			}
		}
		stage('integration test') {
			steps {
				echo "integration test"
			}
		}
	}
	post {
		always {
			echo 'im runing always'
		}
		success {
			echo 'yes its working'
		}
		failure {
			echo 'hoo no!'
		}
	}
}