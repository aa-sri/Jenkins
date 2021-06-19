pipeline { 
    agent any

    stages {
        stage('gitcheckout') {
            steps {
				git branch: 'main', url: 'https://github.com/aa-sri/Jenkins.git'
            }
        }
		stage('docker build & tag') {
			steps {
				sh 'sudo docker build . -t aasri/snowflake:latest'
			}
		}
		stage('docker push') {
			steps {
			    sh 'sudo docker login -u $doc_name -p $doc_pass'
				sh 'sudo docker push aasri/snowflake:latest'
			}
		}
		stage('docker run') {
			steps {
				sh 'sudo docker run aasri/snowflake'
			}
		}
    }
}