pipeline {
    agent any

    parameters {
        string(name: 'S3_BUCKET', defaultValue: 'ci-cd-project-ak', description: 'S3 Bucket for frontend deployment')
    }

    environment {
        // Add AWS CLI path to Jenkins environment
        PATH = "/usr/bin:/usr/local/bin:/bin:/usr/local/aws-cli/v2/2.35.11/dist"
    }

    stages {
        stage('Deploy to S3') {
            steps {
                sh """
                # Verify AWS CLI is accessible
                echo "Current PATH: \$PATH"
                which aws
                aws --version
                
                # Deploy files
                aws s3 cp ./index.html s3://${params.S3_BUCKET}/
                aws s3 cp ./frontend_version.json s3://${params.S3_BUCKET}/
                
                echo "✅ Deployment completed successfully!"
                """
            }
        }
    }
}
