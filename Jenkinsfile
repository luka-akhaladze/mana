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
