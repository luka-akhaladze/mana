pipeline {
    agent any
    parameters {
        booleanParam defaultValue: false, description: 'to not install', name: 'isInstalled'
    }


    environment {
        TARGET_DIR = "/home/jenkins/django_server/"
        VENV_DIR = "${env.TARGET_DIR}myenv"
    }

    stages {
        stage('checkout github') {
            steps {
                script {
                    sh """
                    if [ -d "${env.TARGET_DIR}" ]; then
                        echo "Directory exists. Removing it."
                        rm -rf ${env.TARGET_DIR}
                    fi
                    git clone https://github.com/luka-akhaladze/mana.git ${env.TARGET_DIR}
                    """
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                sh '''
                cd ${TARGET_DIR}
                python3 -m venv ${VENV_DIR}
                bash -c "source ${VENV_DIR}/bin/activate "
                '''
            }
        }
        stage('Install Django if not installed') {
            when {
                expression {
                    return params.isInstalled == false
                }
            }
            steps {
                sh '''
                bash -c "pip install django"
                '''
            }
        }
        stage('Start Server') {
            steps {
                sh '''
                cd ${TARGET_DIR}myproject
                bash -c "python manage.py runserver 0.0.0.0:8000 >> server.log 2>&1 &"
                '''
            }
        }
    }
    post {
        success {
            echo "great success ${env.TARGET_DIR}"
        }
        failure {
            echo "fail"
        }
    }
}
