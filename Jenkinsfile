pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/charan-18-dot/charan.git'
        MAVEN_CMD = 'mvn clean package'
        WAR_FILE = 'target/app.war'
        TOMCAT_USER = 'charan'
        TOMCAT_PASS = 'charan123'
        TOMCAT_URL = 'http://34.205.71.66:8080/manager/text'
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url:https://github.com/charan-18-dot/charan.git 
            }
        }

        stage('Build') {
            steps {
                sh MAVEN_CMD
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy to Tomcat') {
            steps {
                script {
                    def WAR_NAME = 'app'
                    sh """
                    curl -v -u $TOMCAT_USER:$TOMCAT_PASS -T $WAR_FILE $TOMCAT_URL/deploy?path=/$WAR_NAME
                    """
                }
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Deployment Failed!'
        }
    }
}
