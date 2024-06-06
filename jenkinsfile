pipeline {
    agent any
    
    parameters {
        string(name: 'FATHER',
            defaultValue: 'Vader',
            description: 'Select your father')
        text(name: 'PHRASE', defaultValue:
            'it was the best of times, it was the worst of times',
            description: 'Enter your favorite phrase')
        booleanParam(name: 'RUN_TEST',
            defaultValue: false,
            description: 'Toggle this value to run universe')
        choice(name: 'AWS_REGION',
            choices: ['us-central-2b', 'us-east-2c', 'us-west-1a'],
            description: 'Select your region')
        password(name: 'DATABASE_PASSWORD',
            defaultValue: '',
            description: 'Enter your database password')
    }

    stages {
        stage('Test') {
            steps {
                script{
                    echo "I am your ${params.FATHER}"
                    echo "My favorite phrase is '${params.PHRASE}'"
                    echo "Will I rule the universe? ${params.RUN_TEST}"
                    echo "I live in ${params.AWS_REGION}"
                    echo "Can I tell you a secret? ${params.DATABASE_PASSWORD}"
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
