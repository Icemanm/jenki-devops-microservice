pipeline {
	//agent { docker { image 'maven:3.6.3'} }
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:/$mavenHome/bin:$PATH"
	}
	stages{
		stage('Build') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "URL - $env.BUILD_URL"
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