pipeline{
    agent any
    environment { 
        registry = "pavneetkaur15/capstone" 
        registryCredential = 'jenkins-docker' 
        dockerImage = '' 
    }    
    tools { 
        maven 'maven3'
    }
    stages
       {
          stage("Build")
            {
                steps{
                    sh "mvn compile"
                    //echo "hi"
                }
                
            }
            stage("Test")
            {
                steps{
                    sh "mvn clean test"
                }
            }
            stage("Package")
            {
                steps{
                    sh "mvn clean package"
                }
            }
            stage('Building our image') { 
                steps { 
                    script { 
                        dockerImage = docker.build registry + ":$GIT_COMMIT-$BUILD_NUMBER"
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
   //        stage("Deployment----------"){
//                    steps{
//                        withKubeConfig([credentialsId: 'my-kube']){

 //                           sh 'kubectl get all'
                        }
                    }
           }
      }
}
