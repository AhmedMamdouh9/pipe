pipeline {
    agent any 

    stages {
        stage('Requirements') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        

        stage('Docker Login') {
            steps {
                withCredentials([string(credentialsId: 'JENKINS_PASSWORD_1', variable: 'DOCKER_PASSWORD')]) {
                    sh 'echo $DOCKER_PASSWORD | docker login -u ahmedmamdouh51099 --password-stdin'
                }
            }
        }

        stage('Docker Build') { 
            steps {
                sh 'docker build -t ahmedmamdouh51099/pipe:latest .' 
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push ahmedmamdouh51099/pipe:latest'
            }
        }
    }
}