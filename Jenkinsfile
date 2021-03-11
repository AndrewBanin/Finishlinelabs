pipeline { 
    environment { 
        registry = "banina/andrew-boutique" 
        registryCredential = 'dockerhub-jenkins' 
        dockerImage = '' 
    }
    agent any 
    stages { 
        stage('Cloning our Git') { 
            steps { 
                git 'https://github.com/AndrewBanin/Finishlinelabs.git' 
            }
        } 
        stage('Building our image') { 
            steps { 
                script { 
                    sh 'cd staticWebsite'
                    dockerImage = docker.build registry + ":$BUILD_NUMBER" 
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