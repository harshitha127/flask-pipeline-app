pipeline {
    agent any

    environment {
        VENV = "venv"
        PYTHON = "C:\\Program Files\\Python312\\python.exe "
    }

    stages {
        stage('Clone GitHub Repo') {
            steps {
                git branch: 'main', credentialsId: 'github-https', url: 'https://github.com/harshitha127/flask-pipeline-app.git/'
            }
        }

        stage('Set Up Python Virtual Environment') {
            steps {
                bat "${PYTHON} -m venv ${VENV}"
                bat ".\\${VENV}\\Scripts\\python.exe -m pip install --upgrade pip"
                // Either install packages directly:
                bat ".\\${VENV}\\Scripts\\pip install flask pandas numpy tensorflow"
                // OR (better) install from requirements.txt if present:
                // bat ".\\${VENV}\\Scripts\\pip install -r requirements.txt"
            }
        }

        stage('Run Flask App') {
            steps {
                bat ".\\${VENV}\\Scripts\\python app.py"
            }
        }
    }
}







