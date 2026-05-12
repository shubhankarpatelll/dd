pipeline {
    agent any

    environment {
        registry = '4vv23ci070/test4'
        registryCredential = 'jenkin_docker_token'
        dockerimage = ''
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/main']],
                    extensions: [],
                    userRemoteConfigs: [[url: 'https://github.com/Prajna070/dd.git']]
                )
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerimage = docker.build(registry)
                }
            }
        }
    }
}
