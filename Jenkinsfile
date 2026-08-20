pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Build stage is running'
            }
        }

        stage('Test') {
            steps {
                echo 'Test stage is running'
                
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }

        failure {
            echo 'Pipeline failed!'
        }

        always {
            echo 'Pipeline execution finished.'
        }
    }
}
