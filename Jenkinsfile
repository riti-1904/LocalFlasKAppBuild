pipeline {
    agent any
    
    environment {
        FLASK_PORT = "5000"
    }

    stages {
        stage('Checkout Code') {
            steps {
                git url: 'C:\Users\pasar\OneDrive\Desktop\FlaskApp', branch: 'master'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Stop Previous Instance') {
            steps {
                sh "pkill -f 'python3 app.py' || true"
            }
        }

        stage('Run Flask App') {
            steps {
                sh 'nohup python3 app.py &'
            }
        }
    }

    post {
        success {
            echo "Flask application started successfully."
        }
    }
}
