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

    // configure jenkins options
    options {
        // add timestamps to log files
        timestamps()
        //cause the build to timeout if it runs for more than an hour
        timeout(time: 1, unit: 'HOURS')
        // only keep 10 logs for no more than 10 days
        buildDiscarder(logRotator(daysToKeepStr: '10', numToKeepStr: '10'))
    }
    
    triggers {
        // trigger to run pipeline everyday at midnight
        cron '@midnight'
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
        stage ('DEPLOY') {
            steps {
                sh 'echo " Build ID: ${BUILD_ID}" > jenkins-advanced-report.txt'
            }
        }
        stage ('REPORT') {
            steps {
                echo "creating build report..."
                archiveArtifacts allowEmptyArchive: true, artifacts: '*.txt', fingerprint: true, followSymlinks: false, onlyIfSuccessful: true
            }
        }
    }
    // post deployment collection of stages that will only run after all other stages have completed
        post {
            //this stage will ALWAYS run regadless of outcome
            always {
                echo "thanks for using jenkins, goodbye."
            }
        } 
}
