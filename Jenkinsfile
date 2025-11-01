node {
    stage('Checkout') {
        echo 'Checking out source code...'
        checkout scm
    }

    stage('Build') {
        echo 'Building the Spring PetClinic project...'
        bat 'mvn clean package -DskipTests'
    }

    stage('Test') {
        echo 'Running tests...'
        bat 'mvn test'
    }

    echo '✅ Scripted pipeline completed successfully!'
}
