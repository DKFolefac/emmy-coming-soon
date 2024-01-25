pipeline {
    agent any
    
    triggers {
         pollSCM '* * * * *'
    }
    stages {
        stage('Install Dependencies') {
            steps {
                // Use Node.js and npm installed on the Jenkins agent
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                // Build the App
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
