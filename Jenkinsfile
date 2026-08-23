pipeline {
    agent any

    stages {

        stage('Create File') {
            steps {
                sh '''
                    echo "Jenkins Artifact Practical" > report.txt
                    echo "Build completed successfully" >> report.txt
                    echo "This file is created by Jenkins" >> report.txt
                '''
            }
        }

        stage('Archive Artifact') {
            steps {
                archiveArtifacts artifacts: 'report.txt', fingerprint: true
            }
        }

    }

    post {
        success {
            echo 'Artifact archived successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }
    }
}
