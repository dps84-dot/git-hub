pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Build is running...'
            }
        }

        stage('Test') {
            steps {
                catchError(
                    buildResult: 'SUCCESS',
                    stageResult: 'FAILURE'
                ) {
                    echo 'Test is running...'

                    // Intentionally failing command
                    sh 'exit 1'
                }
            }
        }

        stage('Next Stage') {
            steps {
                echo 'Pipeline continued after error handling'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
