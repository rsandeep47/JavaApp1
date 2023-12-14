pipeline {
    agent any

    stages {
        stage('CLONE SCM') {
            steps {
                echo 'Cloing code from GITHUB'
				git branch: 'main', url: 'https://github.com/rsandeep47/JavaApp1.git'
            }
        }
		 stage('Build artifact') {
            steps {
                echo 'Build artifact using maven'
				sh 'mvn clean install'
            }
        }
		 stage('Deploy') {
            steps {
                echo 'Deploy app to Tomcat Applicaton Server'
				deploy adapters: [tomcat9(credentialsId: 'TomcatCred', path: '', url: 'http://54.89.174.2:8082/')], contextPath: 'MyJavaApp2', war: '**/*.war'
            }
        }
    }
}
