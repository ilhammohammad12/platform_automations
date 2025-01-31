pipeline {
    agent any
    environment {
        ANSIBLE_HOST_KEY_CHECKING = "False"
    }
    stages {
        stage('checkout code') {
            steps {
                git branch: 'main', url: 'https://github.com/ilhammohammad12/platform_automations.git'
            }
        }
        stage('Run ansible playbook') {
            steps {
                script {
                    // Using sshagent to run commands on the remote node
                    sshagent(['my-ssh-key']) {
                        sh """
                            ssh -o StrictHostKeyChecking=no root@192.168.1.200 'ansible-playbook /opt/ansible/platform_automations/site.yml'
                        """
                    }
                }
            }
        }
    }
}
