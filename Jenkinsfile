
pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/charan-18-dot/charan.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'  // Modify for Node.js: 'npm install', Python: 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'  // Modify for Node.js: 'npm test', Python: 'pytest'
            }
        }

        stage('Deploy') {
            steps {
                echo "🚀 Deploying application..."
                // Add deployment steps (Docker/Kubernetes/EC2)
            }
        }
    }

    post {
        success {
            echo "✅ CI/CD Pipeline executed successfully!"
        }
        failure {
            echo "❌ Build failed! Check logs for details."
        }
    }
}
