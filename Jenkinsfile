pipeline {
    agent any

    environment {
        // Define the SSH credentials ID
        SSH_CREDENTIALS_ID = 'my-ssh-key'  // Change this to your Jenkins credentials ID
        REMOTE_SERVER = '192.168.1.200' // The target remote server IP
        ANSIBLE_PLAYBOOK = '/opt/ansible/platform_automations/site.yml' // Path to your playbook
        
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the source code
                checkout scm
            }
        }

        stage('Run Ansible Playbook') {
            steps {
                script {
                    // Use the SSH agent to pass the credentials for the SSH connection
                    sshagent([SSH_CREDENTIALS_ID]) {
                        // Run Ansible command to run the playbook
                        sh """
                            ansible-playbook  ${ANSIBLE_PLAYBOOK} --ssh-common-args='-o StrictHostKeyChecking=no'
                        """
                    }
                }
            }
        }
    }

    post {
        success {
            echo "Ansible playbook ran successfully."
        }

        failure {
            echo "Ansible playbook execution failed."
        }
    }
}
