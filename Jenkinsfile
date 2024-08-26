pipeline {
    agent any

    stages {
        stage('clone') {
            steps {
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/satyapujari06/CandyStore.git']]) 
            }
        }
        stage('docker') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-cred') {
                         sh 'docker build -t sree/candystore .'
                         sh 'docker push sree/candystore:latest'
                   }
               }
            }
        }
    }
}
