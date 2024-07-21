pipeline {
    agent any
    stages {
        stage('Environment Info') {
            steps {
                sh 'echo "Environment Variables:"'
                sh 'env'
                sh 'echo "Node.js Version:"'
                sh 'node -v || echo "Node.js not installed"'
                sh 'echo "npm Version:"'
                sh 'npm -v || echo "npm not installed"'
                sh 'echo "Which Node.js:"'
                sh 'which node || echo "Node.js not found"'
                sh 'echo "Which npm:"'
                sh 'which npm || echo "npm not found"'
                sh 'echo "OS Info:"'
                sh 'uname -a'
                sh 'lsb_release -a || echo "lsb_release command not found"'
                sh 'echo "Installed Packages:"'
                sh 'dpkg -l || rpm -qa || echo "Package manager not found"'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
    }
}
