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

					parallel(
      a: {
        
		def jmxFileName = "${params.JMX_FILE_NAME}"
		def jenkinsParameters = "${params.JENKINS_PARAMETERS}"
                bat "docker run -t -v D:\\QIQ\\courses\\Run_From_CMD:/data jmeter_devops ${jmxFileName}"
      },
      b: {
        echo "This is branch b"
	echo "This is branch bb"
	echo "This is branch bbb"
	echo "This is branch bbbb"      
      }
    )
				}
			}
        }
		
		}
	  post {
        always {
          bat "docker system prune --all"
	  bat "Y"	
    steps {
        deleteDir()
    }

        }
	}
 }
