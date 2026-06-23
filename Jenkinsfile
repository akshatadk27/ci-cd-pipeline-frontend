pipeline {
    agent any

    parameters {
        string(name: 'S3_BUCKET', defaultValue: 'ci-cd-project-ak', description: 'S3 Bucket for frontend deployment')
    }

    environment {
        PATH = "$PATH:/usr/local/bin"
        AWS_DEFAULT_REGION = 'us-east-1'
        BUCKET = "${params.S3_BUCKET}"
    }

    stages {
        stage('Deploy to S3') {
            steps {
                sh """
                aws s3 cp ./index.html s3://$BUCKET/
                aws s3 cp ./frontend_version.json s3://$BUCKET/
                """
            }
        }
    }
}
