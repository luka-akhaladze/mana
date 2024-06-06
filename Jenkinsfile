pipeline {
    agent any

    environment {
        TARGET_DIR = "/etc/django_server/" // Set your target directory here
    }

    stages {
        stage('checkout github') {
            steps {
                script {
                    // Clone the repository
                    sh """
                    if [ -d "${env.TARGET_DIR}" ]; then
                        echo "Directory exists. Removing it."
                        rm -rf ${env.TARGET_DIR}
                    fi
                    git clone https://github.com/username/repo.git ${env.TARGET_DIR}
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
