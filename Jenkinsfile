pipeline {
    agent any

    stages {

        environment {
            TARGET_DIR = "/etc/djano_server/" 
        }
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
            post {
                success {
                    echo "great success ${env.TARGET_DIR}"
                }
                failure {
                    echo "fail"
                }
            }
            }
        }

    //     stage('Deploy') {
    //         when {
    //             environment name: 'ENVIRONMENT', value: 'DEVELOPMENT'
    //         }
    //         steps {
    //             echo 'Hello World from deploy'
    //         }
    //     }

    //     stage('Report') {
    //         steps {
    //             script {
    //                 writeFile file: 'changelog.txt', text: params.CHANGELOG

    //                 echo "Changelog:\n${params.CHANGELOG}"
                    
    //                 if (params.CHANGELOG.contains('urgent')) {
    //                     echo 'Urgent changes detected!'
    //                 }
    //             }
    //         }
    //     }
    }
}
