pipeline {
    agent any  
    stages {
        stage ("Sonar quality check") {
            agent {
                docker {
                    image 'openjdk:11'
                    RUN mkdir /home/.sonar
                    RUN chmod 777 /home/.sonar
                    ENV SONAR_USER_HOME=/home/.sonar
                }
            }
            steps{
               script{
                  withSonarQubeEnv(credentialsId: 'stoken') {
                        sh 'chmod +x gradlew'
                        sh 'java -version'
                        sh './gradlew sonarqube --stacktrace'
                    }
               }
            }
        }
    }
}
