pipeline {
	//agent { docker { image 'maven:3.6.3'} }
	agent any
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:/$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile') {
			steps {
				sh "mvn clean compile"
			}
		}
		stage('test') {
			steps {
				sh "mvn test"
			}
		}
		stage('integration test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Peckage') {
			steps {
				sh "mvn packege -DskipTests"
			}
		}
		stage('Build Docker image') {
			steps {
				script {
					dockerImage = docker.BUILD("icemanm/currency-exchange-microservice:$env.BUILD_TAG")
				}
			}
		}
		stage('Push Docker image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');

					}
				}
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