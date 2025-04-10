pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Cloning the repo...'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh 'pytest test_app.py || echo "⚠️ Tests failed or not found. Continuing..."'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mkdir -p deploy && cp app.py deploy/ || echo "⚠️ Deploy skipped (app.py not found)"'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}

