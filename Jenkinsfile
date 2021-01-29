pipeline {
	//agent { docker { image 'node:13.8'} }
	agent any
	environment {
		dockerHome = tool 'MyDocker'
		mavenHome = tool 'MyMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"  // Add Mydocker home to $PATH to execute shell /bin scripts
	}
	stages {
		stage('Checkout') { 
			steps { 
				// sh 'node --version'
				// $env.ENV_NAME is used for Jenkins variables
				// $VAR ($PATH) is used for image variable
				echo 'mvn --version'
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
		stage('Compile') { 
			steps { 
				sh "mvn clean compile" // Install dependencies and compiles the code
       }
     }

		stage('Test') { 
			steps { 
				sh "mvn test"
     }
   }

		stage('Integration Test') { 
			steps { 			
				sh 'mvn failsafe:integration-test failsafe:verify'

				}
			}
		stage('Build Docker Image') {
			steps {
				docker build -t "aurond/wrapper:$env.BUILD_TAG"
				//script {
					//dockerImage = docker.build("aurond/wrapper:${env.BUILD_TAG}")
				}
			}
		}

		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub') {
					dockerImage.push();
					dockerImage.push('latest'); 
				}
			}
		 }
		}
	

  }	
}