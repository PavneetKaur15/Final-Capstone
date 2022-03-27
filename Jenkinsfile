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
                    echo "hi"
                }
                
            }
            stage("Test")
            {
                steps{
                    sh "mvn clean test"
                    echo "hi"
                }
            }
            stage("Package")
            {
                steps{
                    sh "mvn clean package"
                }
            }
      }
}
