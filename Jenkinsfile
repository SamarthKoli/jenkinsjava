pipeline {
    agent any

    tools {
        jdk 'JDK21'            // ✅ Change this to match your Jenkins tool name
        maven 'jenkins-maven'  // ✅ Ensure this matches Global Tool Config name
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
