pipeline{
    agent any

    stages{
        stage("Sonar Quality Check"){
            agent {
                 ### to use different versions of build environments (like java 8,java11, java 17 )we need to use docker images
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script {

                    withSonarQubeEnv(credentialsId: 'sonarqube-token') {
                          sh 'chmod +x gradlew'
                          sh './gradlew sonarqube'
                    }

                }
            }
        }
        post{
            always{
                echo "========always========"
            }
        }
    }
}