pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Build is running...'
            }
        }

        stage('Test with Try Catch') {
            steps {
                script {
                    try {
                        echo 'Test is running...'

                        // Intentionally failing command
                        sh 'exit 1'

                    } catch (err) {
                        echo "Test failed, but error was handled."
                    }
                }
            }
        }

        stage('Next Stage') {
            steps {
                echo 'Pipeline continued after error handling.'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
