pipeline {
    agent any
    stages {
        stage('Build Artifacts') {
            steps{
                sh "mvn clean package -DskipTests=true"
                archive "target/*.jar"
            }
        }
        stage('Tests') {
            steps {
                sh "mvn test"
            }
            post{
                always{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    }
}