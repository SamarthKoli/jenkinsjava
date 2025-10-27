pipeline {
    agent any

    tools {
       
        maven 'jenkins-maven' 
    }

    environment {
        JAR_NAME = "jenkinsdemo-1.jar" // ✅ update to match actual JAR name
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
                bat "mvn clean package -DskipTests"
            }
        }

        stage('Execute Application') {
            steps {
                echo "🚀 Running Java Application..."
                bat "java -jar target/${JAR_NAME}"
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
