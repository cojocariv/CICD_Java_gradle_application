pipeline {
    agent any  
    stages {
        stage ("Sonar quality check") {
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
               script{
                  withSonarQubeEnv(credentialsId: 'stoken') {
                        sh 'sudo chmod +x gradlew'
                        sh 'sudo ./gradlew sonarqube --info'
                    }
               }
            }
        }
    }
}
