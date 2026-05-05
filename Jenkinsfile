pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building application...'
                sh 'cd node-app && npm install'
                sh 'cd node-app && npm run build'
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
                        sh 'cd node-app && npm test'
                    }
                }
                stage('Lint') {
                    steps {
                        sh 'cd node-app && npm run lint'
                    }
                }
                stage('Integration') {
                    steps {
                        sh 'cd node-app && npm run integration-tests'
                    }
                }
            }
        }
    }
}
