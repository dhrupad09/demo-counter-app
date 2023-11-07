pipeline{
    
    agent any 
    
    stages {
        
        stage('Git Checkout'){
            
            steps{  
                git branch: 'main', url: 'https://github.com/dhrupad09/demo-counter-app.git'
            }
        }
        stage('UNIT testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn test'
                }
            }
        }
        stage('Integration testing'){
            
            steps{
                
                script{
                    
                    sh 'mvn verify -DskipUnitTests'
                }
            }
        }
        stage('Maven build'){
            
            steps{
                
                script{
                    
                    sh 'mvn clean install'
                }
            }
        }
        stage('Static code analysis'){
            
            steps{
                
                script{
                    
                    withSonarQubeEnv(credentialsId: 'dd') {
                        
                        sh 'mvn clean package sonar:sonar'
                    }
                   }
                    
                }
            }
            stage('upload war file to nexus'){
                
                steps{
                    
                    script{
                        
                        nexusArtifactUploader artifacts: [[artifactId: 'springboot', classifier: '', file: 'target/uber.jar', type: 'jar']], credentialsId: '866994da-a25d-4acb-8117-4c0c6644cffc', groupId: 'com.example', nexusUrl: 'localhost:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'http://localhost:8081/repository/demo-app-release/', version: '1.0.0'
                    }
                }
            }
    }
    
}

