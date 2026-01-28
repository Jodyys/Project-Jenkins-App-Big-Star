pipeline {
    agent any

    environment {
        APP_NAME = "app-big-star"
        CONTAINER_NAME = "app-big-star"
        PORT = "5000"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Jodyys/Project-Jenkins-App-Big-Star.git'
            }
        }

        stage('Test') {
            steps {
                sh '''
                python3 -m venv venv
                . venv/bin/activate
                pip install -r requirements.txt
                pytest || echo "No tests yet"
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t $APP_NAME:latest .
                '''
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop $CONTAINER_NAME || true
                docker rm $CONTAINER_NAME || true

                docker run -d \
                  --name $CONTAINER_NAME \
                  -p $PORT:$PORT \
                  $APP_NAME:latest
                '''
            }
        }
    }

    post {
        success {
            echo "✅ Deploy sukses!"
        }
        failure {
            echo "❌ Pipeline gagal!"
        }
    }
}
