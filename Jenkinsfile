pipeline {
    agent any

    environment {
        // Define variables for Docker image name and tag
        DOCKER_IMAGE = 'auth-module'
        DOCKER_TAG = 'latest'
    }

    stages {
        stage('Clone repository') {
            steps {
                // Cloning GitHub repository
                git 'https://github.com/mrkhmath/Auth-module.git'
            }
        }

        stage('Build Docker image') {
            steps {
                // Building Docker image from the Dockerfile in the cloned repo
                script {
                    docker.build("${DOCKER_IMAGE}:${DOCKER_TAG}", '.')
                }
            }
        }

        stage('Run Docker container') {
            steps {
                // Running the Docker container from the built image
                script {
                    docker.run("${DOCKER_IMAGE}:${DOCKER_TAG}")
                }
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            // Add steps to clean up after pipeline execution if necessary
        }
        success {
            echo 'Pipeline executed successfully.'
        }
        failure {
            echo 'Pipeline execution failed.'
        }
    }
}
