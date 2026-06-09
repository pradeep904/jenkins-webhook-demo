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



// pipeline {

//     agent any

//     stages {
//         stage('credentials test'){
//             steps {
//                 withCredentials([
//                     string(
//                         credentialsId: 'github-token',
//                         variable: 'TOKEN'
//                     )
//                 ]){
//                     sh 'echo Token Loaded' 
//                 }
//             }
//         }
//     } 

//     post {
//         success {
//             archiveArtifacts artifacts: 'target/*.jar'
//         }
//     }   

// }




// Sonarqube 
pipeline {

    agent any

    stages {

        stage('Build'){

            steps {
                sh 'mvn clean package'
            }
        }

        stage('SonarQube Analysis'){

            steps {
                withSonarQubeEnv('sonarqube'){
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Quality Gate'){
            steps {
                timeout(time:2, unit: 'MINUTES'){
                    waitForQualityGate abortPipeline: true
                }
            }
        }
    }
}