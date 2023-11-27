pipeline {
    agent any 
    
    tools{
        jdk 'jdk11'
        maven 'maven3'
    }
    
    stages{
        
        stage("Git Checkout"){
            steps{
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/pavankumarindian/jenkins-sonarqube-java-pipeline.git'
            }
        }
    
        stage("Sonarqube Analysis "){
            steps{
                    sh "mvn clean package"
                    sh ''' mvn sonar:sonar -Dsonar.url=http://3.110.77.78/:8080/ -Dsonar.login=squ_02df3097f97cab62f1c07cd13bb9111f4617b69f -Dsonar.projectName=Petclinic \
                    -Dsonar.java.binaries=. \
                    -Dsonar.projectKey=Petclinic '''
    
                }
            }
        }
}
