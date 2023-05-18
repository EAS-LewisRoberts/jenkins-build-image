CODE_CHANGES = getGitChanges()
pipeline {
    agent any
    options {
        timeout(time: 1, unit: 'SECONDS')
    }
    docker {
        image ''
        label ''
        args ''  
    } 
 
    stages {
        stage ('Build') {
            when {
                expression {
                    env.BRANCH_NAME == 'dev' && CODE_CHANGES == true
                }
            }
            steps{
                echo 'building the application...'
            }
        }
        stage ('Recieve') {
            steps{
                echo 'recieving the application...'
            }
        }
        stage ('Test') {
            when {
                expression {
                    env.BRANCH_NAME == 'dev' || BRANCH_NAME == 'master'
                }
            }
            steps{
                echo 'testing the application...'
            }
        }
        stage ('Deploy') {
            steps{
                echo 'deploying the application...'
            }
        }
    }
}
}
