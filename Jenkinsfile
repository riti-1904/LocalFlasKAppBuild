pipeline {
    agent any
    
    environment {
        FLASK_PORT = "5000"
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    echo "Cloning the repository..."
                    git url: 'C:\Users\pasar\OneDrive\Desktop\FlaskApp', branch: 'master'
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    echo "Installing dependencies..."
                    sh 'pip3 install -r requirements.txt'
                }
            }
        }

        stage('Stop Previous Instance') {
            steps {
                script {
                    echo "Stopping previous Flask instance (if any)..."
                    sh "pkill -f 'python3 app.py' || true"
                }
            }
        }

        stage('Run Flask App') {
            steps {
                script {
                    echo "Starting Flask application..."
                    sh 'nohup python3 app.py &'
                }
            }
        }
    }

    post {
        success {
            script {
                echo "Flask application started successfully."
            }
        }
        failure {
            script {
                echo "Build failed!"
            }
        }
    }
}
