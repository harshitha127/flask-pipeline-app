pipeline {
    agent any

    environment {
        VENV = "venv"
        PYTHON = "\"C:\\Program Files\\Python312\\python.exe\""
    }

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git branch: 'main', credentialsId: 'github-https', url: 'https://github.com/harshitha127/flask-pipeline-app.git'
            }
        }

        stage('Set Up Python Virtual Environment') {
            steps {
                bat "${PYTHON} -m venv ${VENV}"
                bat ".\\${VENV}\\Scripts\\python.exe -m pip install --upgrade pip"
                bat ".\\${VENV}\\Scripts\\pip install -r requirements.txt"
            }
        }

        stage('Run Flask App') {
            steps {
                bat ".\\${VENV}\\Scripts\\python.exe app.py"
            }
        }
    }

    post {
        always {
            echo 'Cleaning up workspace...'
            bat 'taskkill /F /IM python.exe || exit 0'
            cleanWs()
        }
    }
}
