pipeline {
    agent any  // Runs on any available Jenkins agent

    environment {
        VENV_DIR = "venv"  // Define virtual environment directory
    }

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url:'https://github.com/harshith363/jenkins-python.git'
            }
        }

        stage('Setup Python Virtual Environment') {
            steps {
                sh 'python3 -m venv $VENV_DIR'  // Create virtual environment
                sh '. $VENV_DIR/bin/activate && pip install --upgrade pip'  // Activate venv and upgrade pip
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '. $VENV_DIR/bin/activate && pip install -r requirements.txt'
            }
        }

        stage('Run Python Script') {
            steps {
                sh '. $VENV_DIR/bin/activate && python script.py'
            }
        }
    }

    post {
        always {
            sh 'rm -rf $VENV_DIR'  // Clean up virtual environment after execution
        }
    }
}
