pipeline {
    
     agent { node { label 'AGENT-1' } } //you can keep any server name here, I have my agent-1 server so, given that 
     options {
        timeout(time: 1, unit: 'HOURS') 
    }

    // this is the cron tab for the trigger automatic build for every 10 min 
    triggers {
        cron('*/10 * * * *')
    }
    //environament concept
    environment {
        USER = 'Nishal'
    }

    //parameters
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
                sh 'ls -latr'
                sh 'pwd'
                sh 'printenv'
               
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                sh '''
                ls -ltr
                pwd
                date
                time
                echo "This is for testing the multiple steps"
                echo "This is the response testing the github webhook and jenkins connection setup"
                '''
                 

            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }

        //authorization concept using the environments
        stage('Example') {
            environment {
                AUTH = credentials('ssh-auth')
            }
            steps {
                sh 'printenv'
            }
        }


        // this is the parameters value which it is calling the above params
        stage('Params') {
            steps {
                echo "Hello ${params.PERSON}"

                echo "Biography: ${params.BIOGRAPHY}"

                echo "Toggle: ${params.TOGGLE}"

                echo "Choice: ${params.CHOICE}"

                echo "Password: ${params.PASSWORD}"
            }
        }

        //

        stage('Example') {
            input {
                message "Should we continue?"
                ok "Yes, we should."
                submitter "alice,bob"
                parameters {
                    string(name: 'PERSON', defaultValue: 'Mr Jenkins', description: 'Who should I say hello to?')
                }
            }
            steps {
                echo "Hello, ${PERSON}, nice to meet you."
            }
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
