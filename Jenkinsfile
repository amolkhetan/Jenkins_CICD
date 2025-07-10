pipeline {
    agent any

    environment {
        VENV = "${WORKSPACE}/venv"
    }

    stages {
        stage('Build') {
            steps {
                echo "Setting up Python environment and installing dependencies..."
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Deploy') {
            when {
                expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
            }
            steps {
                echo "Deploying Flask App..."
                sh '''
                    . venv/bin/activate
                    nohup python app.py &
                '''
            }
        }
    }

    post {
        success {
            echo "Build #${env.BUILD_NUMBER} succeeded for job '${env.JOB_NAME}'."
        }
        failure {
            echo "Build #${env.BUILD_NUMBER} failed for job '${env.JOB_NAME}'."
        }
    }
}
