pipeline {
	agent docker { image 'maven:3.6.3'} 
	stages{
		stage('Build') {
			steps {
				sh 'mvn --version'
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