pipeline {
    agent any
    tools {
        // This tool name must match the name you configured in Manage Jenkins > Tools
        jdk 'JDK-21' 
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/BernardHwang/hello-java-2.git'
            }
        }
        stage('Build') {
            steps { 
                sh 'chmod +x ./gradlew'
                sh './gradlew build'
            }
        }
        stage('Test') {
            steps { sh './gradlew test'} 
        }
        stage('Deploy') {
            steps { 
                sh 'java -jar build/libs/hello-world-java-V1.jar'
            }           
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
