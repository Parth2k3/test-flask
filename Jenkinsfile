
pipeline {
    agent any

    environment {
        VENV = 'venv'
    }

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main', url: 'https://github.com/parth2k3/test-flask.git'
            }
        }

        stage('Set up Python Virtual Env') {
            steps {
                sh 'python -m venv $VENV'
                sh './$VENV/bin/pip install --upgrade pip'
                sh './$VENV/bin/pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh './$VENV/bin/python -m unittest discover -s tests'
            }
        }
    }

    post {
        always {
            junit 'tests/**/TEST-*.xml' // if you export test results
        }
    }
}
