pipeline {
    agent any
    tools {
        jdk 'JDK17'
        gradle 'gradle-8.5'
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
                sh 'java  --version'
                sh 'gradle --version'
            }
        }
	
        stage('Build') {
            steps {
                sh 'gradle clean build'
		echo 'Building'
            }
        }
        stage('Test') {
            steps {
		sh 'gradle test'
                sh 'gradle jacocoTestReport'
		 echo 'Testing'
            }
        }
        stage('Archive') {
            steps {
                echo 'Archiving'
		archiveArtifacts artifacts: "build/*", fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
}

