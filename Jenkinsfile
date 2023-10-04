pipeline {
    agent { node { label 'AGENT-1' } } //you can keep any server name here, I have my agent-1 server so, given that 

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
            }
        }
    }
}