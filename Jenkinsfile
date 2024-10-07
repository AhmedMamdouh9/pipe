pipeline {
    agent any 

    stages {
        stage('Requirements And Test') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install -r requirements.txt
                echo "test"
                '''
            }
        }
        

        stage('Docker Login') {
            steps {
                withCredentials([string(credentialsId: 'DOCKER_PASSWORD', variable: 'JENKINS_PASSWORD_3')]) {
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