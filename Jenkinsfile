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
                    python3 -m venv venv
                    source venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Run Tests') {
            steps {
                sh 'source venv/bin/activate && pytest test_app.py'
            }
        }

        stage('Deploy') {
            steps {
                sh 'mkdir -p deploy && cp app.py deploy/'
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
