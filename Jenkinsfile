pipeline {
	agent {label 'agent'}

	stages {
		stage('Deploy') {
		steps {
		ansiblePlaybook(
			colorized: true,
			credentialsId: 'ssh-cred',
			inventory: "hosts",
			playbook: "playbook.yml"
			)
		}
		}
		stage('Wait for Nginx restart') {
		 steps {
		  sleep 20 // seconds
		}
		}
		stage('Connection checks (http requests') {
		 steps {
		  script {
		    def nginx_ip = sh(script: 'curl -sI 192.168.56.115:85', returnStdout: true)
                        
                   // def response = sh(script: 'curl -sI ' + nginx_ip, returnStdout: true)
                    echo nginx_ip
	        }
               }
	      }
	     }
            }
