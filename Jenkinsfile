pipeline {
    agent any

    tools {
        maven 'Maven'   // Make sure 'Maven' is configured in Jenkins Global Tools
        jdk 'JDK17'     // Use JDK17 or whatever you configured
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the Spring PetClinic application...'
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh 'mvn test'
            }
        }
    }

    post {
        success {
            echo '✅ Build and Test stages completed successfully!'
        }
        failure {
            echo '❌ Build failed! Please check errors in Console Output.'
        }
    }
}
