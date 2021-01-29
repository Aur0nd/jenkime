pipeline {
	agent { docker { image 'node:13.8'} }
	stages {
		stage('Build') { 
			steps { 
				sh 'node --version'
				echo "Build"
	}
}
		stage('Test') { 
			steps { 
				echo "Test"
 }
}

		stage('Integration Test') { 
			steps { 			
				echo "Integration Test"

				}
			}
		} 

	post {
		always {
			echo 'All stages were run'
		}
		
		success {
			echo 'Stages were successful'					
		}
		failure {
			echo 'Stages failed'
		}
	}
}