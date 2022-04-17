pipeline {
	agent any

	stages{
		stage('Build'){
			steps {
				echo 'Running build...'
				sh './gradelew build --no daemon'
				archiveArtifacts artifacts: 'dist/trainSchedule.zip'
			}
		}
		stage('DeployToStaging'){
			when{
				branch 'master'
			}			
			steps {
				echo "Deploying... ${env.BUILD_ID} on ${env.JENKINS_URL}"
			}
		}
	}
}
