pipeline {
    agent any

    stages {

        stage('Build') {
            steps {
                sh './gradlew clean build'   // Gradle build
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'   // Run tests (already included in build, but okay to keep)
            }
        }

        stage('Run Application') {
            steps {
                sh 'java -jar build/libs/MyGradleApp.jar'   // Run generated JAR
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
