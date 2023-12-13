pipeline {
    agent any
    
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
                        inventory: '/home/vagrant/playbook/inventory'
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

