pipeline {
    agent any

    tools {
        jdk 'JDK-17'        // Jenkins → Global Tool Configuration ka name
        maven 'Maven-3.9'   // same yahan
    }

    stages {

        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build & Test') {
            steps {
                bat 'mvn clean test'
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'target/**', allowEmptyArchive: true
        }
        success {
            echo '✅ Tests executed successfully'
        }
        failure {
            echo '❌ Tests failed'
        }
    }
}
