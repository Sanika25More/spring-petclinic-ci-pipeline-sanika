node {
    try {
        stage('Preparation') {
            echo 'Cleaning workspace before starting...'
            deleteDir()  // cleans previous build files

            echo 'Checking out the source code...'
            checkout([$class: 'GitSCM',
                      branches: [[name: '*/main']],
                      userRemoteConfigs: [[url: 'https://github.com/Sanika25More/spring-petclinic-ci-pipeline-sanika.git']]
            ])
        }

        stage('Build') {
            echo 'Building the Spring PetClinic project using Maven...'
            bat 'mvnw clean install'
        }

        stage('Test') {
            echo 'Running unit tests...'
            bat 'mvnw test'
        }

        stage('Deploy') {
            echo 'Deploying application...'
            // Example: Copy WAR file or start server (optional)
            echo 'Application deployed successfully!'
        }

    } catch (err) {
        echo "❌ Build failed due to: ${err}"
        currentBuild.result = 'FAILURE'
        throw err
    } finally {
        stage('Post Actions') {
            if (currentBuild.result == 'SUCCESS') {
                echo '✅ Build completed successfully!'
            } else {
                echo '⚠️ Build failed. Check the logs for errors.'
            }

            // Archive build artifacts for review
            archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true

            // Always clean up after build
            cleanWs()
        }
    }
}
