pipeline {
    agent any
    
    environment {
        MY_STR = 'Hi, this is Timur....'
        CONSTANT = 999
    }

    parameters {
        string ( name: 'VERSION',
            defaultValue: 'xxx.xxx.xxx',
            description: 'Enter upgrade version number: ')

        choice ( name: 'ENVIRONMENT',
            choices: ['PROD','DEV','TST'],
            description: 'Enter deployment environment name: ')

        booleanParam ( name: 'RUN_TEST',
            defaultValue: false,
            description: 'checkbox to run pre-deployement tests: ' )
    }
    
    stages {
        stage ('PREP') {
            steps {
                echo "gathering requirements..."

            }
        }
        stage ('BUILD') {
            steps {
                echo "starting the build process..."

            }
        }
    }
}
