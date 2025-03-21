pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "charancherry576/python-docker-app"
        DOCKER_TAG = "latest"
    }

    stages {
        stage('Clone Repository') {
            steps {
                git ' https://github.com/charan-18-dot/charan.git'
            }
        }

        stage('Build Application') {
            steps {
                sh 'echo "Building the application..."'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:$DOCKER_TAG .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: 'https://hub.docker.com/r/charancherry576/charan']) {
                    sh 'docker push $DOCKER_IMAGE:$DOCKER_TAG'
                }
            }
        }

        stage('Deploy Container') {
            steps {
                sh 'docker run -d -p 8081:80 $DOCKER_IMAGE:$DOCKER_TAG'
            }
        }
    }
}
