pipeline {
    agent any
    tools {
        maven 'Maven'  // Ensure Maven is configured in Jenkins
        jdk 'JDK'      // Ensure Java is configured in Jenkins
    }
    stages {
        stage('Initialize') {
            steps {
                echo "Setting up environment..."
            }
        }
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }
    }
    post {
        always {
            junit allowEmptyResults: true, testResults: '**/target/surefire-reports/*.xml'
            echo 'Build and test completed!'
        }
    }
}
