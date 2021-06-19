pipeline { 
    agent any

    stages {
        stage('gitcheckout') {
            steps {
				git branch: 'main', url: 'https://github.com/aa-sri/Jenkins.git'
            }
        }
		stage('docker build') {
			steps {
				sh 'sudo docker build . -t aasri/snowflake1:latest'
			}
		}
		stage('docker tag') {
			steps {
				sh 'sudo docker tag aasri/snowflake1:latest aasri/snowflake2:latest'
			}
		}
		stage('docker push') {
			steps {
			    sh 'sudo docker login -u $doc_name -p $doc_pass'
				sh 'sudo docker push aasri/snowflake2:latest'
			}
		}
		stage('docker run') {
			steps {
				sh 'sudo docker run aasri/snowflake2'
			}
		}
    }
}