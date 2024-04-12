pipeline{
	agent any
	stages{
		stage('gitcheckout'){
		  steps{
			git 'https://github.com/Nithishkumar0064/new-java-project.git'
		    }
		}
		stage('build'){
			steps{
			 sh "mvn clean install"
			}
		}
		stage('archive'){
			steps{
			 archiveArtifacts artifacts: 'target/*.war'
			}
		}
		stage('Monitoring'){
			steps{
			 echo "Being monitored by prometheus"
			}
		}
	}
}
