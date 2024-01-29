pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                // Build your Android project
                sh './gradlew assembleDebug'
            }
        }

        stage('Test') {
            steps {
                // Run your tests
                sh './gradlew test'
            }
        }

        stage('Deploy') {
            steps {
                // Deploy the application (e.g., upload to an app distribution platform)
                // Add your deployment steps here
            }
        }

        stage('Generate APK') {
            steps {
                // Generate the APK file
                sh './gradlew assembleRelease'
                archiveArtifacts artifacts: '**/*.apk', fingerprint: true
            }
        }
    }

    post {
        success {
            // Notify or perform additional actions on success
            echo 'Build, test, deploy, and APK generation succeeded!'
        }

        failure {
            // Notify or perform additional actions on failure
            echo 'Build, test, deploy, or APK generation failed!'
        }
    }
}
