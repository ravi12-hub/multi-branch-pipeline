pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'npm install'
                sh 'npm run build'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'dist/**', fingerprint: true
                }
            }
        } // <--- Added this missing brace to close the Build stage

        stage('sucessfull') {
            steps {
                echo '7 croreeeeeeee'
            }
        } 
    }
}