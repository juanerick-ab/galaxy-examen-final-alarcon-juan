pipeline {
    agent any

    stages {
        // stage('Build') {
        //     agent {
        //         docker { image 'maven:3.6.3-openjdk-11-slim' }
        //     }
        //     steps {
        //         sh 'mvn package'
        //     }
        //     post {
        //         success {
        //             archiveArtifacts artifacts: 'target/labmaven-*.jar', fingerprint: true, onlyIfSuccessful: true
        //         }
        //     }
        // }
        stage('Build') {
            agent {
                docker { image 'maven:3.6.3-openjdk-11-slim' }
            }
            steps {                        
                sh 'mvn -B verify'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true, onlyIfSuccessful: true                        
            }
        }
    }
}