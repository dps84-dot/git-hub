pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Build is running...'
            }
        }

        stage('Timeout Test') {
            options {
                timeout(time: 10, unit: 'SECONDS')
            }

            steps {
                echo 'Starting long-running task...'
                sleep 20
                echo 'Task completed.'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
