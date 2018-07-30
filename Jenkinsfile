pipeline {


    agent { node { label 'master' } }


    stages {
        // Parallel execution
        stage('Run process') {
            steps {
                parallel (
                    Thread1: {
                        sh "echo Thread 1 running with option ${option}"
                    },
                    Thread2: {
                        sh "echo Thread 2 running with option ${option}"
                    }
                )
            }
        }

        stage('Finish') {
            steps {
                echo "Build finished"
            }
        }
    }

    // Post build actions
    // Make sure you have email server configured to allow sending mail from Jenkins
    post {
        always {
            echo "Always run..."
        }

        success {
            echo "Send success e-mail..."
        }

        failure {
            echo "Send failure e-mail..."
        }
    }
}
