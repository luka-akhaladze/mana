pipeline {
    agent any
    parameters {
        booleanParam defaultValue: false, description: 'to not install', name: 'isInstalled'
    }


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
                cd /home/jenkins/django_server/
                python3 -m venv myenv
                source myenv/bin/activate
                '''
            }
        }
        stage('install django if its not'){
            when{
                expression {
                    return params.isInstalled == false
                }
            }
            steps{
                sh "pip install django"
            }
        }
        stage('Start server') {
            steps {
                sh '''
                cd myproject
                python manage.py runserver
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
