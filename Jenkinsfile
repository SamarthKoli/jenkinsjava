pipeline {
    agent any

    tools {
       
        maven 'jenkins-maven' 
    }

    environment {
        JAR_NAME = "app.jar" // ✅ update to match actual JAR name
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/SamarthKoli/jenkinsjava.git'
            }
        }

        stage('Build') {
            steps {
                sh "mvn clean package -DskipTests"
            }
        }

        stage('Execute Application') {
            steps {
                echo "🚀 Running Java Application..."
                sh "java -jar target/${JAR_NAME}"
            }
        }
    }

    post {
        success {             // ✅ Correct spelling
            echo "✅ Java Application executed successfully!"
        }
        failure {
            echo "❌ Build Failed — Check logs!"
        }
    }
}
