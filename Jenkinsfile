pipeline {
    agent any

    stages {
        stage('Clone GitHub') {
            steps {
                echo 'Source code from our GitHub'
				git branch: 'main', url: 'https://github.com/DevSecOpsEasy/Resources.git'
            }
        }
		
		
		stage('Build') {
            steps {
                echo 'Building the code with Maven'
				sh 'mvn clean install'
            }
        }
		
		stage('Deploy') {
            steps {
                echo 'Deploy .war file to our Tomcat server'
				deploy adapters: [tomcat9(credentialsId: '1ad35925-a4c0-4c7b-af2b-8ea7158689cf', path: '', url: 'http://54.91.53.172:8080/')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
