pipeline {
    agent any

    environment {
        VENV_DIR = 'venv'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/Rameshyadav55/indian-traffic-ai-main.git'
            }
        }

        stage('Install Python & Create Virtual Env') {
            steps {
                sh '''
                sudo apt-get update
                sudo apt-get install -y python3 python3-pip python3-venv

                python3 -m venv ${VENV_DIR}
                . ${VENV_DIR}/bin/activate

                pip install --upgrade pip
                pip install flask opencv-python ultralytics
                '''
            }
        }

        stage('Run Application') {
            steps {
                sh '''
                . ${VENV_DIR}/bin/activate
                python3 app.py
                '''
            }
        }
    }
}
