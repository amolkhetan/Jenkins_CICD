pipeline {
  agent any

  environment {
    VENV = 'venv'
  }

  stages {
    stage('Build') {
      steps {
        sh 'python3 -m venv $VENV'
        sh '. $VENV/bin/activate && pip install -r requirements.txt'
      }
    }

    stage('Test') {
      steps {
        sh '. $VENV/bin/activate && pytest'
      }
    }

    stage('Deploy') {
      when {
        expression { currentBuild.result == null || currentBuild.result == 'SUCCESS' }
      }
      steps {
        sh '. $VENV/bin/activate && nohup python app.py &'
        echo 'App deployed to staging!'
      }
    }
  }

  post {
    success {
      mail to: 'amol.khetan@gmail.com',
           subject: "✅ Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
           body: "Build and deployment completed successfully. 🎉"
    }

    failure {
      mail to: 'amol.khetan@gmail.com',
           subject: "❌ Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
           body: "Build encountered errors. Please check Jenkins console output for details."
    }
  }
}

