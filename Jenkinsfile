pipeline {
	agent {label 'agent'}

	stages {
		stage('Deploy'){
		steps{
		ansiblePlaybook(
			colorized: true,
			credentialsId: 'ssh-cred',
			inventory: "hosts",
			playbook: "playbook.yml"
			)
		}
		stage('Wait for Nginx restart'){
		 steps{
		  sleep 20 // seconds
		}
		}
		stage('Connection checks (http requests'){
		 steps{
		  script {
		    def nginx_ip = sh(script: "docker inspect --format '{{ .NetworkSettings.IPAddress }}' nginx-balancer", returnStdout: true)
                        
                    def response = sh(script: 'curl -sI ' + nginx_ip, returnStdout: true)
                    echo response
	        }
                }
		}
