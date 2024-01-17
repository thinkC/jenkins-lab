pipeline {
    agent any
        environment {
        ANSIBLE_SSH_CREDENTIALS = credentials('ansible-access1')
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/thinkC/jenkins-lab.git'
            }
        }

        // stage('Patch Linux Server') {
        //     steps {
        //         ansiblePlaybook credentialsId: 'ansible-access1', installation: 'Ansible on jenkins01', inventory: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/inventory', playbook: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/example.yml', vaultTmpPath: ''
        //     }
        // }
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
