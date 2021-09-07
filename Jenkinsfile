import hudson.model.*;

println env.JOB_NAME
println env.BUILD_NUMBER

pipeline {
    
    stages {
	
	stage('git checkout') { 
            steps{
				 script{
				 checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '81e5e57a-73b3-486e-a38a-e0d1a3ffb872', url: 'https://github.com/join20170910/simple-java-maven-app.git']]])
					  }
		       }
		 }
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
		stage('Deliver') {
            steps {
                sh './deliver.sh'
            }
        }
    }
}
