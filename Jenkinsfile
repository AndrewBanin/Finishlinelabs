pipeline { 
    environment { 
        registry = "banina/andrew-boutique" 
        registryCredential = 'dockerhub-jenkins' 
        dockerImage = '' 
        AWS_ACCESS_KEY_ID     = credentials('aws_jenkins_connection')
        AWS_SECRET_ACCESS_KEY = credentials('aws_jenkins_connection')
        AWS_DEFAULT_REGION = ('us-east-1')
    }
    agent any 
    stages { 
       stage('Building our image') { 
            steps { 
               dir ('staticWebsite') { 
                script { 
                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 
                  }
                }
            } 
        }
        stage('Deploy our image') { 
            steps { 
                script { 
                    docker.withRegistry( '', registryCredential ) { 
                        dockerImage.push() 
                    }
                } 
            }
        } 
        stage('Cleaning up') { 
            steps { 
                sh "docker rmi $registry:$BUILD_NUMBER" 
            }
             } 
        stage('Cloudformation') {
            steps {
              dir ('staticWebsite') { 
               sh "aws cloudformation create-stack --template-body 'file://dockercft.yaml.yml' --stack-name 'docker-compose' --region 'us-east-1' --parameter ParameterKey=KeyName,ParameterValue=Finishlinelab ParameterKey=InstanceType,ParameterValue=t2.micro" 
              }
            }
        }
    }
}


   