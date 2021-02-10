pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws_jenkins_connection')
        AWS_SECRET_ACCESS_KEY = credentials('aws_jenkins_connection')
        AWS_DEFAULT_REGION = ('us-east-1')
    }
    stages {
        stage('Cloudformation build') {
            steps {
                sh "aws cloudformation create-stack --template-body 'file:///var/lib/jenkins/workspace/first-ci-pipeline_finishlinelab3/Finishlinelab3/finishlinelab3infra.yaml' --stack-name 'Finishlinelab3' --region 'us-east-1' --parameter ParameterKey=KeyName,ParameterValue=Finishlinelab ParameterKey=InstanceType,ParameterValue=t2.micro"
            }
        }
        stage('Build') {
            steps {
                echo 'Buildings..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}