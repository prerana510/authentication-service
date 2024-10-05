pipeline {
	agent any 
	tools {
		maven 'my-maven'
		jdk 'my-jdk'
	}
	stages {
		stage('Clone') {
			steps {git url:'https://github.com/prerana510/authentication-service.git',branch:'main'}
		}
		stage('Build') {
			steps {bat "mvn clean install -DskipTests"}
		}
		stage('Test') {
			steps {bat "mvn test"}
		}
    		stage('Deploy') {
			steps {bat "docker build -t authentication-image ." 
             		bat "docker run -p 8090:8090 -d --name authentication-container authentication-image"}
		}
	}
}
