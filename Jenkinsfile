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
                def sshPort = '2201'

                    // Deploy the built React application to the local Ubuntu server using scp
                    script{
                        def scpCmd = """
                            
                            scp -i ${sshKeyPath} -P ${sshPort}  ${buildDirectory}/* ${serverUser}@${serverHost}:${deploymentPath}
                        """
                        sh scpCmd.trim()
                    }
                }
            }

        }
    }
}