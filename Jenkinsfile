// pipeline {

//     agent any

//     stages {

//         stage('Checkout') {
//             steps {
//                 echo 'Checking out source code'
//             }
//         }

//         stage('Build') {
//             steps {
//                 sh 'mvn clean package'
//             }
//         }

//         stage('Test') {
//             steps {
//                 echo 'Running tests'
//             }
//         }

//         stage('Package') {
//             steps {
//                 echo 'Packaging application'
//             }
//         }

//     }

//     post {

//         success {
//             archiveArtifacts artifacts: 'target/*.jar'
//             echo 'Build Successful'
//         }

//         failure {
//             echo 'Build Failed'
//         }

//     }

// }
pipeline {

    agent any

    stages {
        stage('credentials test'){
            steps {
                withCredentials([
                    string(
                        credentialsId: 'github-token',
                        variable: 'TOKEN'
                    )
                ]){
                    sh 'echo Token Loaded' 
                }
            }
        }
    }    

}
