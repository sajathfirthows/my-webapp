env.PATH = "/usr/bin/git:${env.PATH}"
env.GIT_HOME = tool 'git'



pipeline {
    agent any

    stages {
        stage('Checkout Git repository') {
            steps {
                git branch: 'main', url: 'https://github.com/sajathfirthows/my-webapp.git'
            }
        }

        stage('Build Docker image') {
            steps {
                script {
                    docker.build('my-node-app', '.')
                }
            }
        }

        stage('Push Docker image to registry') {
            steps {
                script {
                    docker.withRegistry('https://hub.docker.com/r/sajath/myapp', 'Sajathdocker@1') {
                        docker.image('my-node-app').push()
                    }
                }
            }
        }
    }
}
