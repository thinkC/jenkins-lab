// pipeline {
//     agent any
//         environment {
//         ANSIBLE_SSH_CREDENTIALS = credentials('ansible-access')
//     }
    
//     stages {
//         stage('Checkout') {
//             steps {
//                 git 'https://github.com/thinkC/jenkins-lab.git'
//             }
//         }

//         stage('Patch Linux Server') {
//             steps {
//                 script {
//                     ansiblePlaybook(
//                         colorized: true,
//                         installation: 'Ansible on jenkins01',  
//                         playbook: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/example.yml',
//                         inventory: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/inventory',
//                         credentialsId: ANSIBLE_SSH_CREDENTIALS
                        
//                     )
//                 }
//             }
//         }
//     }

//     post {
//         success {
//             echo 'Patch successful!'
//         }
//         failure {
//             echo 'Patch failed!'
//         }
//     }
// }

///////using with credentials///////


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
                    withCredentials([sshUserPrivateKey(credentialsId: ANSIBLE_SSH_CREDENTIALS, keyFileVariable: 'SSH_KEY')]) {
                        ansiblePlaybook(
                            colorized: true,
                            installation: 'Ansible on jenkins01',
                            playbook: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/example.yml',
                            inventory: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/inventory',
                            keyFileVariable: 'SSH_KEY'
                        )
                    }
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




