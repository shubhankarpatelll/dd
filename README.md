pipeline{
    agent any
        enevironment{
        registry='prajnamr/test4'
        }
    stages{
        stage('checkout'){
        steps{
            git branch:'main',
            url: 'https://github.com/Prajna070/dd.git'
            }
        }
    stage('build image'){
        steps{
            script{
                docker.build("${registry}")
                }
            }
        }
    }
}
