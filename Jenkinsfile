pipeline {
    agent any

    tools {
        jdk 'Java-17'    // Name of JDK configured in Jenkins
        maven 'maven-3.9' // Name of Maven configured in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/AusafMohammed/FirstDeplpy.git'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean package'
            }
        }

        stage('Archive') {
            steps {
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }
    }
}
