pipeline {
pipeline {
    agent any
    
    tools {
        maven 'Maven'
        jdk 'JDK'
    }
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from Git repository
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                // Use bat instead of sh for Windows
                bat 'mvn clean install'
            }
        }
        
        stage('Test') {
            steps {
                bat 'mvn test'
            }
            post {
                always {
                    junit '**/target/surefire-reports/*.xml'
                }
            }
        }
    }
    
    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline execution failed!'
        }
    }
}
