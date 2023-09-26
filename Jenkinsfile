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
    stages{
        stage("Run NODE js script"){
            steps{
                script{
                    //install node js if not already installed
                    def nodejsHome = tool name: 'NodeJS' , type: 'Tool'
                    env.PATH = "${nodejsHome}/bin:${env.PATH}"

                    //Execute the Node.js script
                    sh 'node hello.js'
                }
            }

        }
    }
}