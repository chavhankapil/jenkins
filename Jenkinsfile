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
                sh 'docker build -t kapilchavhan56/helloworld:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
                echo 'Logging in to Docker Hub...'

                withCredentials([
                    usernamePassword(
                        credentialsId: 'dockerhub-credentials',
                        usernameVariable: 'DOCKERHUB_USERNAME',
                        passwordVariable: 'DOCKERHUB_PASSWORD'
                    )
                ]) {

                    sh '''
                    echo "$DOCKERHUB_PASSWORD" | docker login -u "$DOCKERHUB_USERNAME" --password-stdin

                    docker push kapilchavhan56/helloworld:latest
                    '''
                }
            }
        }

        stage('Container Deployment') {
            steps {
                echo 'Creating container from image...'

                sh '''
                docker rm -f helloworld_container || true

                docker run -d \
                --name helloworld_container \
                kapilchavhan56/helloworld:latest
                '''
            }
        }
    }
}