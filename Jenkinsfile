pipeline { 
    agent any

    stages {
        stage('gitcheckout') {
            steps {
                git branch: 'main', credentialsId: 'd12662da-ddb5-4fc0-8366-5032015ac591', url: 'https://github.com/aa-sri/DockerFile'
                git branch: 'main', url: 'https://github.com/aa-sri/DockerFile.git'
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