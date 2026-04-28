pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/YOUR_USERNAME/ci-demo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Building..."'
                sh 'python3 --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest'
            }
        }
    }

    post {
        failure {
            emailext (
                subject: "❌ Build Failed: ${env.JOB_NAME}",
                body: "Something went wrong in pipeline.",
                to: "your-email@gmail.com"
            )
        }
        success {
            echo 'Build Passed ✅'
        }
    }
}
