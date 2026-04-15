pipeline {
    agent any

    tools {
        jdk 'JDK11'   // 👈 MUST match name in Jenkins config
    }

    stages {

        stage('Build') {
            steps {
                sh 'chmod +x gradlew'
                sh './gradlew clean build'
            }
        }

        stage('Run Application') {
            steps {
                sh '''
                JAR=$(ls build/libs/*.jar | head -n 1)
                echo "Running $JAR"
                java -jar $JAR
                '''
            }
        }
    }

    post {
        success {
            echo 'Build successful!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
