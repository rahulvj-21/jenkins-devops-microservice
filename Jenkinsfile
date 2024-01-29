// //Scripted Syntax
// node {
// 		echo "Build"	
// 		echo "Test"
// }

//Declarative Syntax
pipeline {
	agent any
	//using docker as the pipeline agent
	// agent{
	// 	docker{
	// 		image 'maven:3.6.3'
	// 	}
	// }
	environment{
		dockerHome= tool 'myDocker'
		mavenHome= tool 'myMaven'
		PATH= "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	stages{
		stage('Checkout'){
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "PATH - $PATH"
				echo "Build"
			}
		}
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				sh "mvn test"
			}
		}
		stage('Integration Test'){
			steps{
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package'){
			steps{
				sh "mvn package"
			}
		}
		stage('Build Docker Image'){
			steps{
				script{
					dockerImage = docker.build("rahulvj21/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker Image'){
			steps{
				script{
					docker.withRegistry('','dockerhub'){
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
			}
		}
	} 
	post{
		always{
			echo "Im always awesome."
		}
		success{
			echo "I run when you succeed."
		}
		failure{
			echo "I run when you fails."
		}
	}
}
