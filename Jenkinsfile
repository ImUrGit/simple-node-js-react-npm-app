pipeline {
    agent {
        docker {
            image 'node:14' // Use an appropriate Node.js version
        }
    }
    stages {
        stage('Environment Info') {
            steps {
                sh 'echo "Environment Variables:"'
                sh 'env'
                sh 'echo "Node.js Version:"'
                sh 'node -v'
                sh 'echo "npm Version:"'
                sh 'npm -v'
                sh 'echo "Which Node.js:"'
                sh 'which node'
                sh 'echo "Which npm:"'
                sh 'which npm'
                sh 'echo "OS Info:"'
                sh 'uname -a'
                sh 'echo "Installed Packages:"'
                sh 'dpkg -l || rpm -qa'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
    }
}
