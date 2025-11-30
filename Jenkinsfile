pipeline{
    agent any
    stages{
        stage('Checkout'){
            steps{
                checkout scm
            }
        }
        stage('Install Dependencies'){
            steps{
                sh'npm install'
            }
        }
        stage('Run Tests'){
            steps{
                npm test
            }
        }
        stage('Acheive Files'){
            steps{
                archiveArtifacts artifacts: '**/*', onlyIfSuccessful: true
            }
        }
    }
    post{
        success{
            echo 'Build and tests were successful!'
        }
        failure{
            echo 'Build or tests failed.'
        }
    }
}