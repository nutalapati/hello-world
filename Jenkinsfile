pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git 'https://github.com/nutalapati/hello-world.git'
            }
        }
        
        stage('Build') {
            steps {
                // Build the Maven project
                sh 'mvn clean package'
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                // Copy the WAR file to Tomcat webapps directory
                sh 'scp target/*.war deployer@34.222.9.185:/opt/tomcat/webapps/'
            }
        }
    }
}

