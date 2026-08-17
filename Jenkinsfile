pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/dps84-dot/git-hub.git'
            }
        }

        stage('Files') {
            steps {
                sh '''
                    echo "Files downloaded from GitHub:"
                    ls -la
                '''
            }
        }

        stage('Git Commit') {
            steps {
                sh '''
                    echo "Latest Git commit:"
                    git log -1 --oneline
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application...'
            }
        }
    }
}
