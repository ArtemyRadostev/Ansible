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
		}
	}
}
