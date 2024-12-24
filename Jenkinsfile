pipeline {
    agent { node { label  'AGENT-1' } }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh '''
                ls -ltr
                pwd
                echo "Hello script"
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
    }
    post{
        always{
            echo ' i will always run wheather the job is success of not'
        }
        success{
            echo ' when job is success'
        }
        failure{
            echo 'run when failure'
        }
    }
}