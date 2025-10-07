pipeline {
    agent any

    stages {
        stage('Clone') {
    steps {
        git url: 'https://github.com/Yacer514/hello-web.git', branch: 'main'
    }
}

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build('hello-web-image')
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    docker.image('hello-web-image').run('-p 3081:80')
                }
            }
        }
    }
}
