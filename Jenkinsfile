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
        stage("Install Dependencies"){
            steps{
                //Install Node Js dependencies
                sh 'npm install'
            }
        }
        stage("Run Node js script"){
            steps{
                script{

                    //Execute the Node.js script
                    sh 'node hello.js'
                }
            }

        }
    }
}