node {
    stage('Checkout') {
        echo 'Checking out the source code...'
        checkout([$class: 'GitSCM',
                  branches: [[name: '*/main']],
                  userRemoteConfigs: [[url: 'https://github.com/Sanika25More/spring-petclinic-ci-pipeline-sanika.git']]
        ])
    }

    stage('Build') {
        echo 'Building the project using Maven...'
        // Run Maven clean and install
        bat 'mvnw clean install'
    }

    stage('Test') {
        echo 'Running unit tests...'
        // Run Maven tests
        bat 'mvnw test'
    }

    stage('Deploy') {
        echo 'Deployment Stage (can be extended later)...'
    }

    echo 'Pipeline execution completed successfully!'
}
