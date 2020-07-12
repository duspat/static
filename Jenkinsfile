pipeline {
    agent any
    stages {
        stage('Lint HTML') {
            steps {
                sh 'echo "Checking for invalid HTML"'
                sh 'tidy -q -e *.html'
            }
        }
        stage('Upload to AWS') {
            steps {
                withAWS(region:'eu-west-2', credentials: 'aws-static') {
                    sh 'echo "Uploading web content to AWS"'
                    s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'duspat-static-web')
                }
            }
        }
    }
}
