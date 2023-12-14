/////working
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

///////using with credentials not working///////


// pipeline {
//     agent any

//     environment {
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
//                     withCredentials([sshUserPrivateKey(credentialsId: ANSIBLE_SSH_CREDENTIALS, keyFileVariable: 'SSH_KEY')]) {
//                         ansiblePlaybook(
//                             colorized: true,
//                             installation: 'Ansible on jenkins01',
//                             playbook: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/example.yml',
//                             inventory: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/inventory',
//                             keyFileVariable: 'SSH_KEY'
//                         )
//                     }
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


///using snippet generator working



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
//                 ansiblePlaybook credentialsId: 'ansible-access', installation: 'Ansible on jenkins01', inventory: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/inventory', playbook: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/example.yml', vaultTmpPath: ''
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


//////with parameters

pipeline {
    agent any

    parameters {
        string(name: 'ANSIBLE_CREDENTIALS_ID', description: 'Credentials ID for Ansible SSH access')
        string(name: 'ANSIBLE_INSTALLATION', defaultValue: 'Ansible on jenkins01', description: 'Ansible installation name')
        string(name: 'INVENTORY_PATH', defaultValue: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/inventory', description: 'Path to Ansible inventory file')
        string(name: 'PLAYBOOK_PATH', defaultValue: '/var/lib/jenkins/workspace/patch-server-etc-pipeline/example.yml', description: 'Path to Ansible playbook file')
        string(name: 'VAULT_TMP_PATH', defaultValue: '', description: 'Path to Ansible vault temporary file')
        string(name: 'GIT_REPO_URL', defaultValue: 'https://github.com/thinkC/jenkins-lab.git', description: 'URL of the Git repository')
    }
    
    stages {
        stage('Checkout') {
            steps {
                git("${params.GIT_REPO_URL}")
            }
        }

        stage('Patch Linux Server') {
            steps {
                ansiblePlaybook(
                    credentialsId: params.ANSIBLE_CREDENTIALS_ID,
                    installation: params.ANSIBLE_INSTALLATION,
                    playbook: params.PLAYBOOK_PATH,
                    inventory: params.INVENTORY_PATH,
                    vaultTmpPath: params.VAULT_TMP_PATH
                )
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
