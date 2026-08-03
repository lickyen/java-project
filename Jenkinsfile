pipeline{
    agent any
    tools{
        maven 'maven'
    }
    stages{
        stage('code'){
            steps{
                git https://github.com/lickyen/java-project.git
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
                deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', url: 'http://98.84.150.215:8081/')], contextPath: 'netflix', war: 'target/*'
            }
        }
    }
}
