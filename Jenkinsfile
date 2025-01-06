pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checking out code...'
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t my-flask-app .'
            }
        }

        stage('Run Tests') {
            steps {
                echo 'Running tests...'
                // Add test scripts or mock test commands
                sh 'docker run --rm my-flask-app python -c "import app; print(app.home())"'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                sh 'docker run -d -p 5000:5000 --name flask-app my-flask-app'
            }
        }
    }

    post {
        always {
            echo 'Pipeline completed.'
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}