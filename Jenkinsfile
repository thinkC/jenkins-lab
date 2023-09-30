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


pipeline{
    agent any
    tools {
        nodejs 'NodeJS 18'
    }
    stages{
        stage('Checkout'){
            steps{
             //checkout the code from repository
            checkout scm
            }
        }
        stage("Build"){
            steps{
                //Install Node Js dependencies
                sh 'npm install'
                //Build the React application
                sh 'npm run build'
            }
        }
        stage("Deploy to Local Ubuntu Server"){
            steps{
                script{

                    //Define  deployment variables for the local server
                    def serverUser = "jenkins"
                    def serverHost = "192.168.33.12"
                    def deploymentPath = "/home/vagrant/myapp"

                    // directory where the built react application is located
                    def buildDirectory = 'build'

                    // SSH key file (if applicable, leave empty for password authentication)
                    def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

                                    // Optional: Port for SSH (default is 22)
                def sshPort = '22'

                    // Deploy the built React application to the local Ubuntu server using scp
                    script{
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

        }
//         stage("Install Serve Locally") {
//     steps {
//         script {
//                  //Define  deployment variables for the local server
//                     def serverUser = "jenkins"
//                     def serverHost = "192.168.33.12"
//                     def deploymentPath = "/home/vagrant/myapp"

//                     // directory where the built react application is located
//                     def buildDirectory = 'build'

//                     // SSH key file (if applicable, leave empty for password authentication)
//                     def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

//                                     // Optional: Port for SSH (default is 22)
//                 def sshPort = '22'
//             def sshCmd = """
//                 ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} "cd ${deploymentPath} && npm install serve"
//             """
//             sh sshCmd.trim()
//         }
//     }
// }
stage("Install Serve Locally") {
    steps {
        script {

                             //Define  deployment variables for the local server
                    def serverUser = "jenkins"
                    def serverHost = "192.168.33.12"
                    def deploymentPath = "/home/vagrant/myapp"

                    // directory where the built react application is located
                    def buildDirectory = 'build'

                    // SSH key file (if applicable, leave empty for password authentication)
                    def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

                                    // Optional: Port for SSH (default is 22)
                def sshPort = '22'
            def npmPath = sh(
                returnStdout: true,
                script: "ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} 'which npm'"
            ).trim()

            def sshCmd = """
                ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} "${npmPath} install serve"
            """
            sh sshCmd.trim()
        }
    }
}


    //  stage("Start React App on server02") {
    //     steps {
    //         script {
    //            //Define  deployment variables for the local server
    //                 def serverUser = "jenkins"
    //                 def serverHost = "192.168.33.12"
    //                 def deploymentPath = "/home/vagrant/myapp"

    //                 // directory where the built react application is located
    //                 def buildDirectory = 'build'

    //                 // SSH key file (if applicable, leave empty for password authentication)
    //                 def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

    //                                 // Optional: Port for SSH (default is 22)
    //             def sshPort = '22'
    //             // SSH into server02 and start the server
    //             def sshCmd = """
    //                 ssh -i ${sshKeyPath} -p ${sshPort} ${serverUser}@${serverHost} "cd ${deploymentPath} && ./node_modules/.bin/serve -s"
    //             """
    //             sh sshCmd.trim()
    //         }
    //     }
    // }


    stage("Start React App") {
    steps {
        script {
                           //Define  deployment variables for the local server
                    def serverUser = "jenkins"
                    def serverHost = "192.168.33.12"
                    def deploymentPath = "/home/vagrant/myapp"

                    // directory where the built react application is located
                    def buildDirectory = 'build'

                    // SSH key file (if applicable, leave empty for password authentication)
                    def sshKeyPath = '/var/lib/jenkins/.ssh/rsa'

                                    // Optional: Port for SSH (default is 22)
                def sshPort = '22'
            def appDirectory = '/home/vagrant/myapp'

            // Navigate to your app directory
            sh "cd ${appDirectory}"

            // Start the React app using locally installed serve
            sh "npx serve -s ${appDirectory}"
        }
    }
}


    }
}