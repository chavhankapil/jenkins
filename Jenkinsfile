pipeline {
    agent any

    stages {
        stage('Hello') {
            steps {
                echo 'Jenkins Connected Successfully'
            }
        }

        stage('Check Python Version') {
            steps {
                echo 'Checking Python version...'
                sh 'python --version'
            }
        }

        stage('Run Python Script') {
            steps {
                echo 'Running Python script...'
                sh 'python helloworld.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t kapilchavhan/helloworld:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                echo 'Pushing Docker image...'
                sh 'docker push kapilchavhan/helloworld:latest'
            }
        }

        stage('Container Deployment') {
            steps {
                echo 'Creating container from image...'
                sh 'docker run -d --name helloworld_container kapilchavhan/helloworld:latest'
            }
        }
    }
}
