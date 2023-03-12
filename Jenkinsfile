pipeline{

    agent any 
    stages{
           
        stage('Git Checkout'){
            
            steps{
                
               git branch: 'main', url: 'https://github.com/rajdeepsingh642/java-gradle-nexus-helm.git'
                    
                    
                }
        }
        
        
        stage("sonar quality check"){
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
            steps{
                script{
                  withSonarQubeEnv(credentialsId: 'sonar_qube') {

                            sh 'chmod +x gradlew'
                            sh './gradlew sonarqube'
                    }
                                                }

                }
            }
        }
    }        


                
            