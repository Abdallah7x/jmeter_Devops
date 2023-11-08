 pipeline {

     agent any
		
		stages {
			stage('Clone repo') {
				steps {
                git branch: 'main', credentialsId: 'CI_bitbucket_with_password', url: 'https://github.com/Abdallah7x/jmeter_Devops.git'
            }
        }
        stage ('Build test Docker') {
            steps {
                script {
				bat 'docker build -t jmeter_devops ./'
				
                     }
            }
        }
      
        stage ('Run Jmeter Docker') {
            steps {
				script{
		def jmxFileName = "${params.JMX_FILE_NAME}"
		def jenkinsParameters = "${params.JENKINS_PARAMETERS}"
                bat "docker run -t -v C:\Users\Abdallah.Khayrat\Desktop:/data jmeter_devops ${jmxFileName}"
                
				}
			}
        }
		
		}
	}
