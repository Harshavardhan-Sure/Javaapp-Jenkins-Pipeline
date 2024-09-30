pipeline {
    agent any
    
    tools {
        maven 'Maven 3.8.1'
        jdk 'JDK 8'
    }
    
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Harshavardhan-Sure/Javaapp-Jenkins-Pipeline.git'
            }
        }
        
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        
        stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                sh 'java -jar target/hello-jenkins-1.0-SNAPSHOT.jar'
            }
        }
    }
}
