pipeline {
    agent any 

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