pipeline {
    agent any
    
    triggers {
         pollSCM '* * * * *'
    }
    environment {
        CI = false          // do not treat warnings as errors
    }
    stages {
        stage('Install Dependencies') {
            steps {
                // Use Node.js and npm installed on the Jenkins agent
                sh 'npm install'
                sh 'npm install react-scripts@latest' 
                sh 'npm install --save-dev @babel/plugin-proposal-private-property-in-object --legacy-peer-deps' 
                sh 'echo BUILD_NUMBER'
                
            }
        }

        stage('Build') {
            steps {
                // Build the App
                sh 'npm run build'
            }
        } 
        // stage('dockerising) {
            // steps {
                // containerise
                // sh 'docker login -u  DKFolefac      -p
                // sh 'docker build -t Emmyride:

        
            
        
    }

    post {
        success {
            // Define post-build actions,if needed
            emailext body: 'done', subject: 'emmy', to: 'banlonjones@gmail.com fomenkykelly21@gmail.com'
            // For example, you can archive the build artifacts
            archiveArtifacts(allowEmptyArchive: true, artifacts: 'dist/**')
        }
    }
}
