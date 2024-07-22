pipeline {
    agent any
    environment {
        http_proxy = 'http://proxy.server.com:port'
        https_proxy = 'http://proxy.server.com:port'
        HTTP_PROXY = 'http://proxy.server.com:port'
        HTTPS_PROXY = 'http://proxy.server.com:port'
    }
    stages {
        stage('Checkout SCM') {
            steps {
                git url: 'https://github.com/ImUrGit/simple-node-js-react-npm-app.git', branch: 'master'
            }
        }

        stage('OWASP DependencyCheck') {
            steps {
                dependencyCheck additionalArguments: '--format HTML --format XML --cveValidForHours 48', odcInstallation: 'OWASP DependencyCheck'
            }
        }
    }
    post {
        success {
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}
