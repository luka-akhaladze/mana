pipeline {
    agent any

    stages {
        stage('checkout github') {
            steps {

                git branch: 'maser',
                credentialsId: 'github-acctoken',
                url: 'https://github.com/luka-akhaladze/mana'
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
