pipeline {
    agent any

    environment {
        TARGET_DIR = "/home/jenkins/django_server/"
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
                cd /home/jenkins/django_server
                source myenv/bin/activate
                pip install -r requirements.txt
                EOF
                '''
            }
        }
        stage('Start Gunicorn') {
            steps {
                sh '''
                cd /home/jenkins/django_server
                source myenv/bin/activate
                gunicorn --workers 3 --bind 0.0.0.0:8000 your_project_name.wsgi:application
                EOF
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
