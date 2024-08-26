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
                     withDockerRegistry(credentialsId: 'cfcf8e7c-18a2-482a-9b04-c1fece4b6d93') {
                         sh 'docker build -t sree/candystore .'
                         sh 'docker push sree/candystore:latest'
                   }
               }
            }
        }
    }
}
