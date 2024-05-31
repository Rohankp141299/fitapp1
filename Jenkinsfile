pipeline {
    agent any
    
environment {
    dockerhub=credentials('dockerhub')
    }
    
    
    stages {
        
        stage('checkout') {
            steps {
                sh 'sudo rm -rf /var/lib/jenkins/workspace/Fitapppipeline
                sh 'pwd'
                echo 'debug'
                sh 'git clone https://github.com/Rohankp141299/fitapp1.git '
                echo 'code pulled '
            }   
            }
        
        stage('build image') {
            steps {
                sh 'pwd'
                sh 'cd fitapp1'
                sh 'pwd'
                sh 'docker build -t Rohankp141299/fitapp12025 -f /var/lib/jenkins/workspace/Backend_Pipeline/fitapp1/Dockerfile .'
                echo 'fitapp1 image is build '
            }
            }
        
        stage('Docker Login') { 
            steps {
                sh 'echo $dockerhub_PSW | docker login -u $dockerhub_USR --password-stdin'
            }
          }
          
         stage('Docker Push') {  
            steps {
                sh 'docker push Rohankp141299/fitapp12025'
            }
          }
        
        stage('Removing old docker container') {
            steps {
                
                sh 'docker container rm  fitapp1cont -f'
                }
              }
              
        stage('Running the docker container') {
            steps {
                sh 'docker run -d  --name fitapp1cont -p 80:80 Rohankp141299/fitapp12025'
                }
              } 
              
        
    }
}
