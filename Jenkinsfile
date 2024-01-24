pipeline {
    agent any
    
    triggers {
         pollSCM '* * * * *'
    }
    stages {
        stage('Checkout') {
            steps {
                // Check out the source code from your repository
                sh 'git pull https://github.com/DKFolefac/emmy-coming-soon.git/'
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                // Use Node.js and npm installed on the Jenkins agent
                sh 'npm install'
            }
        }

        stage('Build Angular App') {
            steps {
                // Build the Angular app
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                echo "testing"
                sh 'npm run test'
            }
        }
    }

    post {
        success {
            // Define post-build actions, if needed
            emailext body: 'done', subject: 'emmy', to: 'banlonjones@gmail.com fomenkykelly21@gmail.com'
            // For example, you can archive the build artifacts
            archiveArtifacts(allowEmptyArchive: true, artifacts: 'dist/**')
        }
    }
}
