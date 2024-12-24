pipeline {
    agent { node { label  'AGENT-1' } }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
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
                error 'this is failure'
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