pipeline {
    agent any

    tools {
        maven 'Maven3'  // Make sure Jenkins has Maven installed or configured as 'Maven3'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Cloning repository...'
                git branch: 'main', url: 'https://github.com/mel0cious/SpringBootMidterm.git'
            }
        }

        stage('Build') {
            steps {
                echo 'Building Spring Boot project...'
                sh './mvnw clean package -DskipTests'
            }
        }

        stage('Archive Artifact') {
            steps {
                echo 'Archiving JAR file...'
                archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
            }
        }

    }

    post {
        success {
            echo 'Build completed successfully!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
