// Setup the webhook to send the notification to Jenkins Machine

pipeline {
    agent any

    stages {
        stage ('SCM') {
            steps {
                git branch: 'master', url: 'https://github.com/AkshayRajodiya/Sunbeam_Project.git'
            }
        }
        stage ('docker login') {
            steps {
                sh 'echo dckr_pat_z1nFRmG-KYyV_f-HL_rR6yW2IKc | /usr/bin/docker login -u akshayrajodiya --password-stdin'
            }
        }
        stage ('docker build image') {
            steps {
                sh '/usr/bin/docker image build -t akshayrajodiya/project .'
            }
        }
        stage ('docker push image') {
            steps {
                sh '/usr/bin/docker image push akshayrajodiya/project'
            }
        }
        stage ('docker remove container') {
            steps {
                sh '/usr/bin/docker container rm -f project'
            }   
        }
        stage ('docker create container') {
            steps {
                sh '/usr/bin/docker container run -d -p 9090:80 --name project akshayrajodiya/project'
            }
    }
}
}


