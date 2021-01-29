pipeline {
	agent { docker { image 'node:13.8'} }
	environment {
		dockerHome = tool 'MyDocker'
		PATH = "$dockerHome/bin:$PATH"  // Add Mydocker home to $PATH to execute shell /bin scripts
	}
	stages {
		stage('Build') { 
			steps { 
				// sh 'node --version'
				// $env.ENV_NAME is used for Jenkins variables
				// $VAR ($PATH) is used for image variable
				echo 'docker version'
				echo "Build"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "PATH - $PATH"

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