pipeline {
	agent any

	stages{
		stage('Build'){
			steps {
				echo 'Running build...'
				//#sh './gradelew build --no daemon'
				//#archiveArtifacts artifacts: 'dist/trainSchedule.zip'
			}
		}
		stage('Build Docker Image'){
			/* when{
				branch 'master'
			} */
			steps {
				echo 'In the step now......'
				script {
                    app = docker.build("asherfaisal/train-schedule")
                    app.inside {
                        sh 'echo $(curl localhost:8080)'
                    }
                }
			}
		}
		
		stage('DeployToStaging'){
			when{
				branch 'master'
			}			
			steps {
				//echo "Deploying... ${env.BUILD_ID} on ${env.JENKINS_URL}"
				echo "Deploying........."
			}
		}
	}
}
