pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git 'https://github.com/navjoth/jenkins-python-demo.git'
            }
        }
        stage('Setup Environment') {
            steps {
                sh 'python -m venv venv && venv\Scripts\activate'
                sh 'pip install -r requirements.txt || echo "No requirements.txt found"'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'pytest --junitxml=report.xml'
            }
        }
    }
}
