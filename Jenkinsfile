// pipeline{
//     agent any
//     tools{
//         git "Git"
//         stages{
//             stage('Checkout'){
//                 steps{
//                     //checkout git repo
//                     git 'https://github.com/thinkC/jenkins-lab.git'
//                 }
//             }
//             stage('Patch Linux server')
//             steps{
//                 script{
//                     //Run ansible playbook to runLinux server
//                     ansiblePlaybook(
//                         colorized: true,
//                         installation: 'Ansible on ansible-ubuntu1',
//                         playbook: '/home/vagrant/playbook/patch_server.yml',
//                         inventory: '/home/vagrant/playbook/inventory'
//                     )
//                 }
//             }
//         }

//         post{
//             success{
//                 echo 'Patch Successful!'
//             }
//             failure{
//                 echo 'Patch failed!'
//             }
//         }
//     }
// }


/////////////


// pipeline {
//     agent any
    
//     stages {
//         stage('Checkout') {
//             steps {
//                 // Check out your source code from the repository
//                 git 'https://github.com/thinkC/jenkins-lab.git'
//             }
//         }

//         stage('Patch Linux Server') {
//             steps {
//                 script {
//                     // Run Ansible playbook to patch the Linux server
//                     ansiblePlaybook(
//                         colorized: true,
//                         installation: 'Ansible on ansible-ubuntu1', // 
//                         playbook: '/home/vagrant/playbook/patch_server.yml',
//                         inventory: '/home/vagrant/playbook/inventory'
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


/////////////////





pipeline {
    // agent any  // Commented out or removed since Ansible is executed on the Ansible server
    
    stages {
        stage('Checkout') {
            steps {
                // Check out your source code from the repository
                git 'https://github.com/thinkC/jenkins-lab.git'
            }
        }

        stage('Patch Linux Server') {
            steps {
                script {
                    // Run Ansible playbook to patch the Linux server
                    dir('/home/vagrant/playbook/') {
                        ansiblePlaybook(
                            colorized: true,
                            installation: 'Ansible on ansible-ubuntu1',
                            playbook: 'patch_server.yml',  // Assuming the playbook is in the same directory
                            inventory: 'inventory'
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
