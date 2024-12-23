pipeline {
    agent { node { label 'AGENT-1' } }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
              sh '''
                ls -ltr
                pwd
                echo " hello Script"
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
        post { 
        always { 
            echo 'I will always run weather the job is run or not'
        }
        success{
            echo ' i will run only when job is success'
        }
        failure{
            echo 'i will run when failure'
        }
    }

}