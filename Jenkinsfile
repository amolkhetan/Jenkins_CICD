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
                echo "Running tests..."
                sh '''
                    . venv/bin/activate
                    pytest --disable-warnings
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

   # post {
   #     success {
   #         mail to: 'munisheak@gmail.com',
   #              subject: "Build Success - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
   #              body: "Great! Build ${env.BUILD_NUMBER} succeeded."
   #    
   #     }
   #     failure {
   #         mail to: 'munisheak@gmail.com',
   #              subject: "Build Failed - ${env.JOB_NAME} #${env.BUILD_NUMBER}",
   #              body: "Oops! Build ${env.BUILD_NUMBER} failed. Please check Jenkins logs."
   #     }
   # }

    post {
        success {
            echo "🎉 Build #${env.BUILD_NUMBER} succeeded for job '${env.JOB_NAME}'."
        }
        failure {
            echo "❌ Build #${env.BUILD_NUMBER} failed for job '${env.JOB_NAME}'."
        }
    }
}
