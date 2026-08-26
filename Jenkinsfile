pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'test', 'prod'],
            description: 'Select deployment environment'
        )
    }

    environment {
        APP_NAME = 'my-app'
    }

    stages {

        stage('Build') {
            steps {
                echo "Building ${APP_NAME}"
                sh 'echo "Build completed" > build.txt'
            }
        }

        stage('Parallel Test') {
            parallel {

                stage('Unit Test') {
                    steps {
                        echo 'Running Unit Tests...'
                        sh 'sleep 3'
                        echo 'Unit Tests Passed'
                    }
                }

                stage('Code Check') {
                    steps {
                        echo 'Running Code Check...'
                        sh 'sleep 3'
                        echo 'Code Check Passed'
                    }
                }
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'build.txt', fingerprint: true
            }
        }

        stage('Approval') {
            when {
                expression {
                    params.ENVIRONMENT == 'prod'
                }
            }

            steps {
                input message: 'Deploy to Production?', ok: 'Proceed'
            }
        }

        stage('Deploy') {
            when {
                expression {
                    params.ENVIRONMENT == 'dev' ||
                    params.ENVIRONMENT == 'test' ||
                    params.ENVIRONMENT == 'prod'
                }
            }

            steps {
                echo "Deploying ${APP_NAME} to ${params.ENVIRONMENT}"
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
