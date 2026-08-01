pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('code'){
            steps{
                git 'https://github.com/Ritesh-Prasad/java-project.git'
            }
        }
        stage('Build'){
            steps{
                sh 'mvn compile'
            }
        }
        stage('Test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('Artifacts'){
            steps{
                sh 'mvn package'
            }
        }
        stage('tomcat'){
            steps{
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://34.234.64.49:8081/')], contextPath: 'netflix', war: 'target/*'
            }
        }
    }
}
