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
		stage('Build'){
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "PATH - $PATH"
				echo "Build"
			}
		}
		stage('Test'){
			steps{
				echo "Test"
			}
		}
		stage('Integration Test'){
			steps{
				echo "Integration Test"
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
