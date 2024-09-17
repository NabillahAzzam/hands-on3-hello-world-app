
pipeline {
    agent any
    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/NabillahAzzam/hands-on3-hello-world-app.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("hands-on3-hello-world-app")
                }
            }
        }
        stage('Run Unit Tests') {
            steps {
                script {
                    dockerImage.inside {
                        sh 'npm install'
                        sh 'npm test'
                    }
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    dockerImage.run('-p 3000:3000')
                }
            }
        }
    }
}
