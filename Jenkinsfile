// pipeline{
//     agent any

//     stages{
//         stage("Run Python script"){
//             steps{
//                 sh "python3 hello.py"
//             }
//         }
//     }
// }

//almost worked

// pipeline{
//     agent any
//     tools {
//         nodejs 'NodeJS 18'
//     }
//     stages{
//         stage('Checkout'){
//             steps{
//              //checkout the code from repository
//             checkout scm
//             }
//         }
//         stage("Build"){
//             steps{
//                 //Install Node Js dependencies
//                 sh 'npm install'
//                 //Build the React application
//                 sh 'npm run build'
//             }
//         }
//         stage("Deploy to Local Ubuntu Server"){
//             steps{
//                 script{

//                     //Define  deployment variables for the local server
//                     def serverUser = "jenkins"
//                     def serverHost = "192.168.33.12"
//                     // def deploymentPath = "/home/vagrant/myapp"
//                     def deploymentPath = "/home/jenkins/myapp"

//                     // directory where the built react application is located
//                     def buildDirectory = 'build'

//                     // SSH key file (if applicable, leave empty for password authentication)
//                     def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

//                                     // Optional: Port for SSH (default is 22)
//                 def sshPort = '22'

//                     // Deploy the built React application to the local Ubuntu server using scp
//                     script{
//                         def scpCmd = """
                            
//                            scp -i ${sshKeyPath} -P ${sshPort} \\
//                             ${buildDirectory}/asset-manifest.json \\
//                             ${buildDirectory}/favicon.ico \\
//                             ${buildDirectory}/index.html \\
//                             ${buildDirectory}/logo192.png \\
//                             ${buildDirectory}/logo512.png \\
//                             ${buildDirectory}/manifest.json \\
//                             ${buildDirectory}/robots.txt \\
//                             ${serverUser}@${serverHost}:${deploymentPath}
//                         """
//                         sh scpCmd.trim()
//                     }
//                 }
//             }

//         }


// // stage("Install Serve Locally") {
// //     steps {
// //         script {
// //             // Define deployment variables for the local server
// //             def serverUser = "jenkins"
// //             def serverHost = "192.168.33.12"
// //             def deploymentPath = "/home/vagrant/myapp"

// //             // SSH key file (if applicable, leave empty for password authentication)
// //             def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

// //             // Optional: Port for SSH (default is 22)
// //             def sshPort = '22'

// //             def nodePath = '/home/vagrant/.nvm/versions/node/v18.18.0/bin/node' 
// //             def npmCmd = """
// //                 ${nodePath} /home/vagrant/.nvm/versions/node/v18.18.0/bin/npm install -g serve
// //             """
// //             def sshCmd = """
// //                 ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} '${npmCmd}'
// //             """
// //             sh sshCmd.trim()
// //         }
// //     }
// // }

// stage("Install Serve Locally") {
//     steps {
//         script {
//                         // Define deployment variables for the local server
//             def serverUser = "jenkins"
//             def serverHost = "192.168.33.12"
//             // def deploymentPath = "/home/vagrant/myapp"
//             def deploymentPath = "/home/jenkins/myapp"

//             // SSH key file (if applicable, leave empty for password authentication)
//             def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

//             // Optional: Port for SSH (default is 22)
//             def sshPort = '22'
//             def sshCmd = """
//                 ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} "source ~/.nvm/nvm.sh && nvm use v18.18.0 && cd ${deploymentPath} && npm install serve"
//             """
//             sh sshCmd.trim()
//         }
//     }
// }





//     //  stage("Start React App on server02") {
//     //     steps {
//     //         script {
//     //            //Define  deployment variables for the local server
//     //                 def serverUser = "jenkins"
//     //                 def serverHost = "192.168.33.12"
//     //                 def deploymentPath = "/home/vagrant/myapp"

//     //                 // directory where the built react application is located
//     //                 def buildDirectory = 'build'

//     //                 // SSH key file (if applicable, leave empty for password authentication)
//     //                 def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

//     //                                 // Optional: Port for SSH (default is 22)
//     //             def sshPort = '22'
//     //             // SSH into server02 and start the server
//     //             def sshCmd = """
//     //                 ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} "cd ${deploymentPath} && ./node_modules/.bin/serve -s"
//     //             """
//     //             sh sshCmd.trim()
//     //         }
//     //     }
//     // }


//     stage("Start React App") {
//     steps {
//         script {
//                            //Define  deployment variables for the local server
//                     def serverUser = "jenkins"
//                     def serverHost = "192.168.33.12"
//                     // def deploymentPath = "/home/vagrant/myapp"
//                     def deploymentPath = "/home/jenkins/myapp"

//                     // directory where the built react application is located
//                     def buildDirectory = 'build'

//                     // SSH key file (if applicable, leave empty for password authentication)
//                     def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

//                                     // Optional: Port for SSH (default is 22)
//                 def sshPort = '22'
//             // def appDirectory = '/home/vagrant/myapp'
//             def appDirectory = "/home/jenkins/myapp"

//             // // Navigate to your app directory
//             // sh "cd ${appDirectory}"

//             // // Start the React app using locally installed serve
//             // sh "npx serve -s ${appDirectory}"

//             def sshCmd = """
//             ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} "cd ${deploymentPath} && /home/vagrant/.nvm/versions/node/v18.18.0/bin/serve -s"
           
//         """
//         sh sshCmd.trim()
//         }
//     }
// }


//     }
// }


//getting errors
// pipeline {
//     agent any
//     tools {
//         nodejs 'NodeJS 18'
//     }
//     stages {
//         stage('Checkout') {
//             steps {
//                 // Checkout the code from the repository
//                 checkout scm
//             }
//         }
//         stage('Setup NVM and Build') {
//             steps {
//                 script {
//                     // Set up NVM environment
//                     def nvmHome = '/home/jenkins/.nvm'
//                     def nvmScript = "${nvmHome}/nvm.sh"
//                     def nvmLoadCmd = "[ -s \"$nvmScript\" ] && \\. \"$nvmScript\""
//                     sh nvmLoadCmd

//                     // Change to your project directory
//                     def projectDir = "/home/jenkins/myapp"
//                     dir(projectDir) {
//                         // Install Node.js dependencies
//                         sh 'npm install'
//                         // Build the React application
//                         sh 'npm run build'
//                     }
//                 }
//             }
//         }
//         stage('Deploy to Local Ubuntu Server') {
//             steps {
//                 script {
//                     // Define deployment variables for the local server
//                     def serverUser = "jenkins"
//                     def serverHost = "192.168.33.12"
//                     def deploymentPath = "/home/jenkins/myapp"

//                     // Directory where the built React application is located
//                     def buildDirectory = 'build'

//                     // SSH key file (if applicable, leave empty for password authentication)
//                     def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

//                     // Optional: Port for SSH (default is 22)
//                     def sshPort = '22'

//                     // Deploy the built React application to the local Ubuntu server using scp
//                     def scpCmd = """
//                         scp -i ${sshKeyPath} -P ${sshPort} \\
//                             ${buildDirectory}/asset-manifest.json \\
//                             ${buildDirectory}/favicon.ico \\
//                             ${buildDirectory}/index.html \\
//                             ${buildDirectory}/logo192.png \\
//                             ${buildDirectory}/logo512.png \\
//                             ${buildDirectory}/manifest.json \\
//                             ${buildDirectory}/robots.txt \\
//                             ${serverUser}@${serverHost}:${deploymentPath}
//                     """
//                     sh scpCmd.trim()
//                 }
//             }
//         }
//         stage('Start React App') {
//             steps {
//                 script {
//                     // Navigate to your project directory
//                     def projectDir = "/home/jenkins/myapp"
//                     dir(projectDir) {
//                         // Start the React app (adjust the command as needed)
//                         sh 'npm start'
//                     }
//                 }
//             }
//         }
//     }
// }


pipeline {
    agent any
    tools {
        // Define a custom NodeJS tool named 'NodeJS 18' for Node.js version 18.0.0
        nodejs 'NodeJS 18'
    }
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                checkout scm
            }
        }
        stage("Build") {
            steps {
                // Install Node.js dependencies
                sh 'npm install'
                // Build the React application
                sh 'npm run build'
            }
        }
        stage("Deploy to Local Ubuntu Server") {
            steps {
                script {
                    // Define deployment variables for the local server
                    def serverUser = "jenkins"
                    def serverHost = "192.168.33.12"
                    def deploymentPath = "/home/jenkins/myapp"
                    def buildDirectory = 'build'
                    def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'
                    def sshPort = '22'

                    // Deploy the built React application to the local Ubuntu server using scp
                    def scpCmd = """
                        scp -i ${sshKeyPath} -P ${sshPort} \\
                        ${buildDirectory}/asset-manifest.json \\
                        ${buildDirectory}/favicon.ico \\
                        ${buildDirectory}/index.html \\
                        ${buildDirectory}/logo192.png \\
                        ${buildDirectory}/logo512.png \\
                        ${buildDirectory}/manifest.json \\
                        ${buildDirectory}/robots.txt \\
                        ${serverUser}@${serverHost}:${deploymentPath}
                    """
                    sh scpCmd.trim()
                }
            }
        }

stage("Install Serve Locally") {
    steps {
        script {
            // Define deployment variables for the local server
            def serverUser = "jenkins"
            def serverHost = "192.168.33.12"
            def deploymentPath = "/home/jenkins/myapp"
            def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'
            def sshPort = '22'

            // Source NVM to ensure Node.js and NPM from NVM are used
            def nvmCmd = "source /home/jenkins/.nvm/nvm.sh"
            def npmCmd = "/home/jenkins/.nvm/versions/node/v18.0.0/bin/npm"

            // Install the 'serve' package globally using Node.js version 18.0.0
            def serveInstallCmd = "${nvmCmd} && ${npmCmd} install -g serve"

            // Execute the serve installation command remotely
            def sshCmd = """
                ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} "${serveInstallCmd}"
            """
            sh sshCmd.trim()
        }
    }
}


        // stage("Start React App") {
        //     steps {
        //         script {
        //             // Define deployment variables for the local server
        //             def serverUser = "jenkins"
        //             def serverHost = "192.168.33.12"
        //             def deploymentPath = "/home/jenkins/myapp"
        //             def buildDirectory = 'build'
        //             def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'
        //             def sshPort = '22'

        //             // Start the React app using the 'serve' package with Node.js version 18.0.0
        //             def sshCmd = """
        //                 ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} "cd ${deploymentPath} && $(npm bin)/serve -s ${buildDirectory}"
        //             """
        //             sh sshCmd.trim()
        //         }
        //     }
        // }

        stage("Start React App") {
    steps {
        script {
            // Define deployment variables for the local server
            def serverUser = "jenkins"
            def serverHost = "192.168.33.12"
            def deploymentPath = "/home/jenkins/myapp"
            def buildDirectory = 'build'
            def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'
            def sshPort = '22'

            // Start the React app using the 'serve' package with Node.js version 18.0.0
            def sshCmd = """
                ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} "cd ${deploymentPath} && \$(npm bin)/serve -s ${buildDirectory}"
            """
            sh sshCmd.trim()
        }
    }
}

    }
}
