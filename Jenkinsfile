pipeline {
    agent { node { label 'AGENT-1' } }

    options {
        // Timeout counter starts AFTER agent is allocated
        timeout(time: 15, unit: 'SECONDS')  // Timeout is set for 15 seconds
    }

    environment { 
        USER = 'kumaraswamy'
    }

    parameters {
        string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
        text(name: 'BIOGRAPHY', defaultValue: '', description: 'Enter some information about the person')
        booleanParam(name: 'TOGGLE', defaultValue: true, description: 'Toggle this value')
        choice(name: 'CHOICE', choices: ['One', 'Two', 'Three'], description: 'Pick something')
        password(name: 'PASSWORD', defaultValue: 'SECRET', description: 'Enter a password')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh '''
                ls -ltr
                pwd
                echo "hi ra bullesh from webhook event"
                printenv
                '''
            }
        }

        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }

        stage('params') {
            steps {
                echo "Hello ${params.PERSON}"
                echo "Biography: ${params.BIOGRAPHY}"
                echo "Toggle: ${params.TOGGLE}"
                echo "Choice: ${params.CHOICE}"
                echo "Password: ${params.PASSWORD}"
            }
        }

        stage('Input') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"  // Only Alice or Bob can submit
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${params.PERSON}, nice to meet you."
            }
        }

        // Corrected PROD Deploy stage
        stage('PROD Deploy') {
            when {
                branch 'main'  // This stage will only run on the 'main' branch
            }
            steps {
                echo "Deploying to PROD"
            }
        }
    }

    post {
        always {
            echo 'I will always run whether the job is successful or not.'
        }
        success {
            echo 'This runs when the job is successful.'
        }
        failure {
            echo 'This runs when the job fails.'
        }
    }
}
