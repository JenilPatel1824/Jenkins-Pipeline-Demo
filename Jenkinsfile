pipeline {
    agent { label 'docker-enabled-agent' }
    stages {
        stage('Build Image') {
            steps {
                script {
                    sh 'docker build -t your-docker-image-name .'
                }
            }
        }
        stage('Docker Push') {
            steps {
                script {
                    sh 'docker push your-docker-image-name'
                }
            }
        }
    }
}
