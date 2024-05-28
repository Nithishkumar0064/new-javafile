#!groovy
pipeline {
    environment {
  registry = 'nithishnithi/tomcat2'
  containerName = 'my-container2'
  registryCredentials = 'Docker_credential'
 }
    agent {label'docker'}
    stages{
        stage('git-checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Nithishkumar0064/java-example.git'
            }
        }
        stage('Build docker image'){
            steps {
                   sh 'image = docker.build("${registry}:$BUILD_NUMBER")'
                
            }
        }
        stage('Push image to Hub'){
            steps {
                sh 'echo Registry-push'
                sh '''
                    docker.withRegistry('', registryCredentials) 
                        image.push()
                        image.push('latest')
                     '''
                
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -itd --name ${containerName} -p 8090:8080 ${registry}'
            }
            
        }
        
      }
    }
