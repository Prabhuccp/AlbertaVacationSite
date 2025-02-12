pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'echo "Hello World"'
                sh '''
                    echo "Multiline shell steps work too"
                    ls -lah
                '''
            }
        }

        stage('Upload to AWS') {
            steps {
                withAWS(region: 'us-east-1', credentials: 'prabhu-jenkins') {
                    sh 'echo "Uploading content with AWS creds"'
                    s3Upload(
                        pathStyleAccessEnabled: true, 
                        payloadSigningEnabled: true, 
                        file: '**/*',  // Uploads all files recursively
                        bucket: 'myjenkinss3', 
                        acl: 'BucketOwnerFullControl'  // Grants full control to bucket owner
                    )
                }
            }
        }
    }
}
