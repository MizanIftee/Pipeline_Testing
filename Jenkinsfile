pipeline {
	agent any
	stages {
		stage('git-checkout') {
			steps {
				echo "Checking out form Git Repo";
				git credentialsId: '1eee6640-3255-494d-ae95-7a9475e31b50', url: 'https://github.com/MizanIftee/Pipeline_Testing.git'
			}
		}
		
		stage('Build') {
			steps {
				echo "Building the checked-out project";
				sh label: '', script: '''chmod a+x Build.sh
                sh Build.sh'''
			}
		}
		
		
		stage('Deploy') {
		steps {
				echo "Deploying to stage environment for more tests";
				sh label: '', script: '''chmod a+x Deploy.sh
                sh Deploy.sh'''
				
			}
		}
	}
	
	post {
		always {
			echo "This will always run"
		}
		success {
			echo "This will run only if successful"
		}
		failure {
			echo "This will run only if failed"
		}
		unstable {
			echo "This will run only if the run was marked as unstable"
		}
		changed {
			echo "This will run only if the state of the pipeline has changed"
			echo "For example,if the pipeline was previously failing but is now successful"
		}
	}
}
