pipeline {
    agent any

    tools {
        jdk 'Java-17'      // Must match JDK name in Jenkins
        maven 'maven-3.9'  // Must match Maven name in Jenkins
    }

    stages {
        stage('Checkout') {
            steps {
                echo '📥 Checking out source code from GitHub...'
                git branch: 'main', url: 'https://github.com/AusafMohammed/FirstDeplpy.git'
            }
        }

        stage('Build') {
            steps {
                echo '⚙️ Running Maven build...'
                sh 'mvn clean package -DskipTests'
                echo '✅ Build completed. JAR file should be in target/ directory.'
            }
        }

        stage('Archive') {
            steps {
                echo '📦 Archiving JAR artifact...'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

        stage('Run JAR') {
            steps {
                echo '🚀 Running the built JAR...'
                sh 'java -jar target/firstdeploy-1.0-SNAPSHOT.jar'
                echo '✅ JAR execution finished.'
            }
        }
    }
}
