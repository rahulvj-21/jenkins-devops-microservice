// //Scripted Syntax
// node {
// 		echo "Build"	
// 		echo "Test"
// }

//Declarative Syntax
node {
	agent any
	stages{
		stage('Build'){
			steps{
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
}
