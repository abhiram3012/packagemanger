pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                // Windows uses 'bat' instead of 'sh'
                bat 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                // This will call: npm test --if-present
                bat 'npm test --if-present'
            }
        }

        stage('Archive Files') {
            steps {
                // Archive everything in workspace (simple for lab)
                archiveArtifacts artifacts: '**/*', onlyIfSuccessful: true
            }
        }
    }

    post {
        success {
            echo "Simple Node Build Completed Successfully!"
        }
        failure {
            echo "Build Failed. Check the output."
        }
    }
}
