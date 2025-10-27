pipeline{
    tools{
        jdk:21
        maven 'jenkins-maven'
    }

    environment{
       JAR_NAME="app.jar"
    }

    stages{

        stage('Checkout'){
            steps{
                git branch : 'Main',
                url:'https://github.com/SamarthKoli/jenkinsjava.git'
            }
        }

        stage('Build'){
            steps{
                sh "mvn clean package -DskipTests"
            }
        }

        stage('Execute Application'){
            steps{
                echo "App is running"
                sh "java -jar target/${JAR_NAME}"
            }
        }
    }

    post{
        sucess{
            echo "Java app executed"
        }
        failure{
            echo "Error ocurred"
        }
        
     }
}