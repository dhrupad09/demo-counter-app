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
    }
    
}

