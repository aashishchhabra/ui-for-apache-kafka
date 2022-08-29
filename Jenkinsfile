pipeline {
	agent {
		label 'swarm_manager_1 || swarm_manager_2'
	}
	stages {
		stage("Pull the latest image"){
			steps{
				sh '/usr/local/bin/docker pull provectuslabs/kafka-ui'
			}
		}
		stage("create docker compose file with all environments provided"){
			steps{
				sh 'echo "I will be creating a script that will be creating the docker compose file on runtime for multi cluster setup"'
			}
		}
		stage("Deploy the docker compose to local environment"){
			when{
				branch 'dev'
			}
			steps{
				sh '/usr/local/bin/docker stack deploy --compose-file docker-compose.yml --resolve-image=always'
			}
		}
		stage("Deploy the docker compose to uat envrionment"){
			when{
				branch 'uat'
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
