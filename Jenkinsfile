pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        stage('Deliver') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                script {
                    try {
                        timeout(time: 30, unit: 'MINUTES') {
                            input message: 'Finished using the web site? (Click "Proceed" to continue)'
                        }
                    } catch (err) {
                        echo 'Input timeout or interruption occurred. Proceeding automatically.'
                    }
                }
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
