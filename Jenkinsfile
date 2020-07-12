pipeline {
    agent any
    stages {
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
