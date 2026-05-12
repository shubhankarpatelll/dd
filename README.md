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
------------------------------------------------------------------------------------------------------------------------------------------


slack 
    open slack and login using email
    in channel create your channel naming devops-team1,2,3,4..... and give public and create
    
jenkins

login to jenkins and download the plugins
in jenkins go to manage jenkins-> scroll down and click on plugins and download **slack notification ** or **slack notification plugin**
after downloading reopen the page and go to manage jenkins scroll down and click systems again scroll down slack 
in slack workspace -> vvcegroup
    fro credential +add give global ->secret text ->next 
    go to chrome and url: https://my.slack.com/services/new/jenkins-ci
    search for your channel and click next go to step 3 and copy that copy and paste in secret text
    decription give notify and create
    apply and save


new item and create demo freestyle project okay
add build steps and select Execute Windows batch command type java --version
+add Post-build Actions in that select slack notification in that
    notify sucess
    notify start
    notify every failure
    save and build now
    
    





    create docker folder

create file sample.py -> 

print("Ayush")

create file Dockerfile no.txt -> 

FROM python
WORKDIR /app
COPY . /app
CMD ["python","sample.py"]

python sample.py

docker build -t test_3 .

docker images

docker run --name con3 test_3

docker login

docker tag test_3 majenayu/test_3

docker push majenayu/test_3


same for  prog 2 but after this 

download ->

docker
docker pipeline
docker compose build step
cloudbees docker custom build environment

create doc and select pipeline

in script add this ->

pipeline {
    agent any

    environment {
        registry = 'majenayu/test_3'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Majenayu/dock.git'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    docker.build("${registry}")
                }
            }
        }
    }
}

after this run
