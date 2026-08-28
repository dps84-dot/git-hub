pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Build started'

                script {
                    try {
                        retry(2) {
                            sh 'echo "Build command running..."'
                        }
                    } catch (err) {
                        echo 'Build failed, but pipeline is handling the error.'
                    }
                }
            }
        }

        stage('Parallel Testing') {
            parallel {

                stage('Unit Test') {
                    steps {
                        echo 'Unit tests running...'
                    }
                }

                stage('Security Test') {
                    steps {
                        echo 'Security tests running...'
                    }
                }
            }
        }

        stage('Create Artifact') {
            steps {
                sh '''
                    echo "Jenkins Practical 21" > report.txt
                    echo "Build completed successfully" >> report.txt
                '''

                archiveArtifacts artifacts: 'report.txt',
                                  fingerprint: true
            }
        }

        stage('Approval') {
            steps {
                input message: 'Deploy to Production?', ok: 'Proceed'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application to Production...'
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
