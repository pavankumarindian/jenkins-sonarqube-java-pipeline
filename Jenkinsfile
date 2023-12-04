pipeline{
    agent any
    tools {
        jdk 'jdk17'
        maven 'maven3'
    }
    environment {
        SCANNER_HOME=tool 'sonar-scanner'
        SONAR_HOST_URL = 'http://52.66.24.161:9000'
        SONAR_TOKEN = credentials('Sonar-token')
    }
    stages{
        stage ('clean Workspace'){
            steps{
                cleanWs()
            }
        }
        stage ('checkout scm') {
            steps {
                git 'https://github.com/Aj7Ay/jpetstore-6.git'
            }
        }
        stage ('maven compile') {
            steps {
                sh 'mvn clean compile'
            }
        }
        stage ('maven Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage("Sonarqube Analysis "){
            steps{
                
                sh ''' $SCANNER_HOME/bin/sonar-scanner -Dsonar.projectName=Petshop \
                -Dsonar.java.binaries=. \
                -Dsonar.projectKey=Petshop '''
                }
            
        }
   }
}
