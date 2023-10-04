pipeline {
    agent { node { label 'AGENT-1' } } //you can keep any server name here, I have my agent-1 server so, given that 

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'ls -latr'
                sh 'pwd'
                //error 'This is failure'
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
            echo 'I will always run weather the job is success or not'
        }
        success{
            echo 'I will always run when the job is success'
        }
        failure{
            echo 'I will always run when the job is failure'
        }
    }
}
