pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Build is running...'
            }
        }

        stage('Retry Test') {
            steps {
                retry(3) {
                    echo 'Trying the operation...'

                    // Failure intentionally create kar rahe hain
                    sh 'exit 1'
                }
            }
        }

        stage('Next Stage') {
            steps {
                echo 'Next stage is running...'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
