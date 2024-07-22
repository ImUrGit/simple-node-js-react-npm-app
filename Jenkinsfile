pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                // Correctly specify the repository URL
                git url: 'https://github.com/ImUrGit/simple-node-js-react-npm-app.git', branch: 'master'
            }
        }

        stage('OWASP DependencyCheck') {
            steps {
                // Run OWASP DependencyCheck
                dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
            }
        }
    }
    post {
        success {
            // Publish the dependency check report
            dependencyCheckPublisher pattern: 'dependency-check-report.xml'
        }
    }
}