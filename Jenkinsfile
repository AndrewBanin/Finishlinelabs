pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID     = credentials('aws_jenkins_connection')
        AWS_SECRET_ACCESS_KEY = credentials('aws_jenkins_connection')
        AWS_DEFAULT_REGION = ('us-east-1')
    }
    stages {
        stage('Cloudformation') {
            steps {
             sh "aws cloudformation create-stack --template-body file://var/lib/jenkins/workspace/third_ci_pipeline_finishlineEC2/FinishlineEC2/finishlinelab2infra.yaml --stack-name BaninaInstance --parameters ParameterKey=KeyName,ParameterValue=Finishlinelab ParameterKey=InstanceType,ParameterValue=t2.micro"
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