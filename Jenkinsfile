pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws_jenkins_connection')
        AWS_SECRET_ACCESS_KEY = credentials('aws_jenkins_connection')
        AWS_DEFAULT_REGION = ('us-east-1')
    }
    stages {
        stage('AWS build') {
            steps {
                stage('Cloudformation build') {
            steps {
                sh "aws cloudformation create-stack --template-body 'file:///var/lib/jenkins/workspace/Finishlinelab5/finishlinelab5/finishlinelab5infra.yml' --stack-name 'Finishlinelab5' --region 'us-east-1' --parameters 'file:///var/lib/jenkins/workspace/parameter.json'"
            }
        }
        stage('Build') {
            steps {
                echo 'Building..'
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