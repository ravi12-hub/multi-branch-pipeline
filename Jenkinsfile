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
                    // Archives the build output, similar to GitLab artifacts
                    archiveArtifacts artifacts: 'dist/**', fingerprint: true
                }
            }
        }

        stage('Test') {
            parallel {
                stage('Unit') {
                    steps {
                        sh 'npm test'
                    }
                }
                stage('Lint') {
                    steps {
                        sh 'npm run lint'
                    }
                }
                stage('Integration') {
                    steps {
                        sh 'npm run integration-tests'
                    }
                }
            }
        }
    }
}
