pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Arpan3904/Jenkins-Pipeline-Demo'
            }
        }

        stage('Build Image') {
            steps {
                script {
                    if (isUnix()) {
                        sh 'docker build -t arpan238/dockerpipeline .'
                    } else {
                        bat 'docker build -t arpan238/dockerpipeline .'
                    }
                }
            }
        }

        stage('Docker Push') {
            steps {
                script {
                    def username = 'arpan238'
                    def password = '********'

                    if (isUnix()) {
                        sh "echo ${password} | docker login -u ${username} --password-stdin"
                        sh 'docker push arpan238/dockerpipeline'
                        sh 'docker logout'
                    } else {
                        bat "echo %password% | docker login -u %username% --password-stdin"
                        bat 'docker push arpan238/dockerpipeline'
                        bat 'docker logout'
                    }
                }
            }
        }
    }
}
