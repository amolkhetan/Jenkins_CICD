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

        stage('Test') {
            steps {
                sh './venv/bin/pytest test_app.py'
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
            withCredentials([string(credentialsId: 'SLACK_WEBHOOK', variable: 'WEBHOOK_URL')]) {
                sh '''
                    curl -X POST -H 'Content-type: application/json' --data '{
                      "text": " *Build SUCCESS* - Job: ${env.JOB_NAME} [#${env.BUILD_NUMBER}]\\n ${env.BUILD_URL}"
                    }' $WEBHOOK_URL
                '''
            }
        }
        failure {
            withCredentials([string(credentialsId: 'SLACK_WEBHOOK', variable: 'WEBHOOK_URL')]) {
                sh '''
                    curl -X POST -H 'Content-type: application/json' --data '{
                      "text": " *Build FAILED* - Job: ${env.JOB_NAME} [#${env.BUILD_NUMBER}]\\n ${env.BUILD_URL}"
                    }' $WEBHOOK_URL
                '''
            }
        }
    }
}

/*
    
    post {
        success {
            withCredentials([string(credentialsId: 'SLACK_WEBHOOK', variable: 'WEBHOOK_URL')]) {
                sh '''
                    curl -X POST -H "Content-type: application/json" --data '{
                      "text": " *Build SUCCESS* - Job: ${env.JOB_NAME} [#${env.BUILD_NUMBER}]\\n ${env.BUILD_URL}"
                    }' "$WEBHOOK_URL"
                '''
            }
        }
        failure {
            withCredentials([string(credentialsId: 'SLACK_WEBHOOK', variable: 'WEBHOOK_URL')]) {
                sh '''
                    curl -X POST -H "Content-type: application/json" --data '{
                      "text": " *Build FAILED* - Job: ${env.JOB_NAME} [#${env.BUILD_NUMBER}]\\n ${env.BUILD_URL}"
                    }' "$WEBHOOK_URL"
                '''
                }
            }
        }
}
*/
