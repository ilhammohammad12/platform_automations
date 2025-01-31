pipeline{
    agent any
    environment {
        ANSIBLE_HOST_KEY_CHECKING = "False"
    }
    stages {
        stage('checkout code'){
            steps{
                git branch: 'main', url: 'https://github.com/ilhammohammad12/platform_automations.git'
            }
        }
        stage('Run anisble playbook'){
            steps{
                sh 'ansible-playbook site.yml'
            }
        }
    }
}
