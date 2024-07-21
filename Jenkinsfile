pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/ImUrGit/simple-node-js-react-npm-app.git'
            }
        }
        stage('Build') {
            steps {
                script {
                    // Pull the Docker image
                    sh 'docker pull node:14'

                    // Run npm install inside the Docker container
                    sh 'docker run --rm -v "$PWD":/usr/src/app -w /usr/src/app node:14 npm install'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Run npm test inside the Docker container
                    sh 'docker run --rm -v "$PWD":/usr/src/app -w /usr/src/app node:14 npm test'
                }
            }
        }
    }
}
