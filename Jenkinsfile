pipeline{
    agent any

    stages {
        stage('checkout code'){
            steps{
                git branch: 'main', url: 'https://github.com/ilhammohammad12/platform_automations.git'
            }
        }
        stage('Run anisble playbook'){
            steps{
                sh 'ansible playbook -i inventory site.yml'
            }
        }
    }
}