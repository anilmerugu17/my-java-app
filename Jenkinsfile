pipeline {
    agent any

    // Use the tools configured in Jenkins (OpenJDK21 and Maven3)
    tools {
        jdk 'OpenJDK21'       // Name configured in Jenkins Global Tool Configuration
        maven 'Maven3'        // Name configured in Jenkins Global Tool Configuration
    }

    stages {
        stage('Checkout') {
            steps {
                echo '🔄 Checking out source code...'
                checkout scm    // Pulls code from your GitHub repo configured in Pipeline from SCM
            }
        }

        stage('Build') {
            steps {
                echo '⚙️ Building project with Maven...'
                sh 'mvn clean compile'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Running tests...'
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                echo '📦 Packaging application...'
                sh 'mvn package'
            }
        }

        stage('Post-Build') {
            steps {
                echo '✅ Build, test, and package completed successfully!'
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo '🎉 SUCCESS: Everything worked!'
        }
        failure {
            echo '❌ FAILURE: Something went wrong.'
        }
    }
}

