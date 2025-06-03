// pipeline {
//     agent any

//     stages {
//         // stage('Build') {
//         //     agent {
//         //         docker { image 'maven:3.6.3-openjdk-11-slim' }
//         //     }
//         //         steps {
//         //             sh 'mvn -B verify'
//         //             archiveArtifacts artifacts: 'target/*.jar', fingerprint: true, onlyIfSuccessful: true                        
//         //         }
//         // }
//         stage('SonarQube') {
//             steps {
//                 script{
//                     def scannerHome = tool 'scanner-default'
//                     echo ${scannerHome}
//                     // withSonarQubeEnv('sonar-server') {
//                     //     sh "${scannerHome}/bin/sonar-scanner \
//                     //     -Dsonar.projectKey=labmaven01 \
//                     //     -Dsonar.projectName=labmaven01 \
//                     //     -Dsonar.sources=src/main \
//                     //     -Dsonar.exclusions=**/*.java \
//                     //     -Dsonar.tests=src/test/java"
//                     // }
//                 }
//             }
//         }
//     }
// }

pipeline {
    agent any

    stages {
        stage('Build') {
            agent {
                docker { image 'maven:3.6.3-openjdk-11-slim' }
            }
            steps {
                sh 'mvn -B verify'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true, onlyIfSuccessful: true
            }
        }

        stage('SonarQube') {
            steps {
                script {
                    def scannerHome = tool 'scanner-default'
                    withSonarQubeEnv('sonar-server') {
                        sh "${scannerHome}/bin/sonar-scanner \
                            -Dsonar.projectKey=labmaven01 \
                            -Dsonar.projectName=labmaven01 \
                            -Dsonar.sources=src/main \
                            -Dsonar.tests=src/test/java"
                    }
                }
            }
        }
    }
}