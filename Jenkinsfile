pipeline {
    environment {
        registry = "sandeesh/azure"
        registryCredential = 'docker-creds'
        dockerImage = ''
    }
    agent any
    stages {
        stage ('Cloning Git') {
            steps {
                git branch: 'main', url: 'https://github.com/vakatigireesh/data-persistence-sample.git'
            }
        }
        stage ('Building Image') {
            steps {
                script {
                    dockerImage= docker.build registry
                }
            }
        }
        stage ('Deploy Image') {
            steps {
                script {
                    docker.withRegistry('', registryCredential ) {
                        dockerImage.push()
                    }
                }
            }
        }
    }
}    
