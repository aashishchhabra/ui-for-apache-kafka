pipeline {
	agent any
	stages {
		stage("Pull the latest image"){
			steps{
				sh 'docker pull provectuslabs/kafka-ui'
			}
		}
		stage("create docker compose file with all environments provided"){
			steps{
				sh 'echo "I will be creating a script that will be creating the docker compose file on runtime for multiple cluster setup"'
			}
		}
		stage("Deploy the docker compose to local environment"){
			when{
				branch 'dev'
			}
			steps{
				sh 'docker compose down --rmi all'
				sh 'docker compose up -d'
			}
		}
		stage("Deploy the docker compose to uat envrionment"){
			when{
				branch 'uat'
				agent any
			}
			steps{
				sh 'echo "deploy on uat swarm cluster"'
			}
		}
		stage("Deploy the docker compose on Prod environment"){
			when{
				branch 'main'
			}
			steps{
				sh 'echo "deploy on Prod swarm cluster"'
			}
		}
	}
}
