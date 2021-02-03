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
                sh 'aws cloudformation create-stack --template-body file:///var/lib/jenkins/workspace/Finishlinelab2/Finishlinelab2/finishlinelabinfra.yml --stack-name BaninaInstance --parameter ParameterKey=KeyName,ParameterValue=finishlinelab ParameterKey=InstanceType,ParameterValue=t2.micro'
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