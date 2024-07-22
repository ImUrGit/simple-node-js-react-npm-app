pipeline {
    agent any
    stages {
        stage('Checkout SCM') {
            steps {
                // Correctly specify the repository URL
                git url: 'https://github.com/ImUrGit/simple-node-js-react-npm-app.git', branch: 'master'
            }
        }

        stage('OWASP Dependency-Check Vulnerabilities') {
              steps {
                dependencyCheck additionalArguments: '''
                            -o './'
                            -s './'
                            -f 'ALL'
                            --prettyPrint''', odcInstallation: 'OWASP Dependency-Check Vulnerabilities'

                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
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