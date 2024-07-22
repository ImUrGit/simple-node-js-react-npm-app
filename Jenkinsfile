pipeline {
    agent any
    environment {
        http_proxy = 'http://proxy.server.com:port'
        https_proxy = 'http://proxy.server.com:port'
        HTTP_PROXY = 'http://proxy.server.com:port'
        HTTPS_PROXY = 'http://proxy.server.com:port'
    }
    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ImUrGit/passwordChecker.git', credentialsId: '1'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Dependency Check') {
            steps {
                sh 'npm audit'
            }
        }
        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML --cveValidForHours 48', odcInstallation: 'OWASP DependencyCheck'
            }
        }
        stage('Run Tests') {
            parallel {
                stage('Integration Test') {
                    steps {
                        sh 'npm run test-integration'  // Replace with actual integration test command
                    }
                }
                stage('UI Test') {
                    steps {
                        sh 'npm run test-ui'  // Replace with actual UI test command
                    }
                }
            }
        }
    }
    post {
        always {
            junit 'path/to/your/test-results.xml'  // Replace with actual path to test results
        }
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
