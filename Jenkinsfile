pipeline {
    agent any

    environment {
        S3_BUCKET = 'amit-static-site-demo'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Checking Source Code'
            }
        }

        stage('Deploy to S3') {
            steps {
                withAWS(credentials: 'jenkins-s3-user', region: 'ap-south-1') {

                    sh '''
                    aws s3 cp index.html s3://$S3_BUCKET/
                    aws s3 cp style.css s3://$S3_BUCKET/
                    aws s3 cp app.js s3://$S3_BUCKET/
                    '''

                }
            }
        }
    }
}
