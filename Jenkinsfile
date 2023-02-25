pipeline{
    agent any 
    stages{
        stage("sonar quality check"){
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                   withCredentials([string(credentialsId: 'sonar-qube', variable: 'sonar_token')]) {
    

                            sh 'chmod +x gradlew'
                            sh './gradlew sonarqube'
                    }
                }

                }
            }
        }
    }