pipeline {
    agent any

    stages {

        stage('Clone') {
            steps {
                git 'https://github.com/Kanishka-Trivedi/jenkins-cicd.git'
            }
        }

        stage('Build Docker') {
            steps {
                sh 'docker build -t jenkinscicd .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker stop jenkinscicd-container || true
                docker rm jenkinscicd-container || true

                docker run -d \
                --name jenkinscicd-container \
                -p 3000:3000 \
                jenkinscicd
                '''
            }
        }
    }
}