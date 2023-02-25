pipeline{
    agent any 
    stages{
           
        stage('Git Checkout'){
            
            steps{
                
               git branch: 'main', url: 'https://github.com/rajdeepsingh642/java-gradle-nexus-helm.git'
                    
                    
                }
        }
        
        stage('sonar quality check'){
            agent {
                docker {
                    image 'openjdk:11'
                }
            }
        } 
        stage('docker build image'){
            steps{
                script{
                    sh 'docker build -t 192.168.1.70:8083/springapp:${BUILD_ID} .'

                }
            }
        }
              stage('docker image push nexus'){
            steps{
                script{
                     withCredentials([string(credentialsId: 'nexus-token', variable: 'nexus_creds')]) {
                        sh "docker login -u admin -p $nexus_creds 192.168.1.70:8083"
                        sh 'docker push 192.168.1.70:8083/springapp:${BUILD_ID}'
                        sh 'docker rmi 192.168.1.70:8083/springapp:${BUILD_ID}'
                         sh   'docker image prune -f'  

                }
          
                  }
                    }
        }
              }
           }



                
            