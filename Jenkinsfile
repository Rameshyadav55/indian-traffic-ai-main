pipeline {
    agent any

    environment {
        VENV_DIR = 'venv'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/Rameshyadav55/indian-traffic-ai-main.git'
            }
        }

        stage('Set up Python Virtual Environment') {
            steps {
                sh '''
                python3 -m venv ${VENV_DIR}
                source ${VENV_DIR}/bin/activate
                pip install --upgrade pip
                pip install flask opencv-python ultralytics || echo "Some packages may already be installed"
                '''
            }
        }

        stage('Run Application') {
            steps {
                sh '''
                source ${VENV_DIR}/bin/activate
                python3 app.py
                '''
            }
        }
    }
}
