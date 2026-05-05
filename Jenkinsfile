pipeline {
    agent any

    tools {
        nodejs "NodeJS 25"
    }

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
        }

        stage('sucessfull') {
            steps {
                echo '7 croreeeeeeee'
            }
        } 
    }
}