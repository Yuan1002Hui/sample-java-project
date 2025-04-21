pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/Yuan1002Hui/sample-java-project.git'
            }
        }
        stage('Build') {
            steps { bat 'start gradlew build'}
        }
        stage('Test') {
            steps {  bat 'start gradlew test'}
        }
        stage('Deploy') {
            steps { powershell 'java -jar build/libs/hello-world-javaV1.jar'}
        }
    }
        
    post {
        always {
            echo 'Cleaning up workspace'
            deleteDir() // Clean up the workspace after the build
        }
        success {
            echo 'Build succeeded!!!'
            // You could add notification steps here
        }
        failure {
            echo 'Build failed!'
            // You could add notification steps here
        }
    }
}