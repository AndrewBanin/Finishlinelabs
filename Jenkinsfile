pipeline { 
    environment { 
        registry = "banina/andrew-boutique" 
        registryCredential = 'dockerhub-jenkins' 
        dockerImage = '' 
    }
    agent any 
    stages { 
       stage('Building our image') { 
            steps { 
               dir ('/var/lib/jenkins/workspace/Andrew_Boutique_website1/staticWebsite') { 
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
    }
}