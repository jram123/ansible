node {

	stage('git clone') {
	
	git credentialsId: 'be361626-aaee-4a30-ba41-7aebe9b09daa', url: 'https://github.com/jram123/ansible.git'
	sh label: '', script: '''cd /var/tmp
	rm -rf ansible
	git clone https://github.com/jram123/ansible.git
	cd ansible
	ls -al'''
	}
	
	stage('ansible syntax check') {
	sh label: '', script: '''
	cd /var/tmp/ansible
	ansible-playbook --syntax-check $ansibleplaybookname'''
	}

    stage('Notification') {
        mail from: "jjanakiramu@gmail.com",
                to: "jjanakiramu@rediff.com",
                subject: "ansible deployment status",
                body: "jenkins job ${env.JOB_NAME} -build ${env.BUILD_NUMBER} ${currentBuild.currentResult} ${env.JOB_URL} complete"
}

}
