pipeline {
    agent any
        environment {
        ANSIBLE_SSH_CREDENTIALS = credentials('ansible-access')
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/thinkC/jenkins-lab.git'
            }
        }

        stage('Patch Linux Server') {
            steps {
                script {
                    ansiblePlaybook(
                        colorized: true,
                        installation: 'Ansible on jenkins01',  
                        playbook: '/home/vagrant/playbook/example.yml',
                        inventory: '/home/vagrant/playbook/inventory',
                        credentialsId: ANSIBLE_SSH_CREDENTIALS,
                        disableHostKeyChecking: true
                    )
                }
            }
        }
    }

    post {
        success {
            echo 'Patch successful!'
        }
        failure {
            echo 'Patch failed!'
        }
    }
}

