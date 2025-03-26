pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main', url: 'https://github.com/navjoth/jenkins-python-demo.git'
            }
        }
        stage('Setup Environment') {
            steps {
                powershell '''
                    python -m venv venv
                    .\\venv\\Scripts\\Activate
                    if (Test-Path requirements.txt) {
                        pip install -r requirements.txt
                    } else {
                        Write-Host "No requirements.txt found"
                    }
                '''
            }
        }
        stage('Run Tests') {
            steps {
                powershell 'pytest --junitxml=report.xml'
            }
        }
    }
}
