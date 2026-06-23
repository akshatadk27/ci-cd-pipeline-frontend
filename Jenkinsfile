pipeline {
    agent any

    parameters {
        string(name: 'S3_BUCKET', defaultValue: 'ci-cd-project-ak', description: 'S3 Bucket for frontend deployment')
    }

    stages {
        stage('Deploy to S3') {
            steps {
                sh """
                # Use full path to AWS CLI
                /usr/local/bin/aws s3 cp ./index.html s3://${params.S3_BUCKET}/
                /usr/local/bin/aws s3 cp ./frontend_version.json s3://${params.S3_BUCKET}/
                """
            }
        }
    }
}
