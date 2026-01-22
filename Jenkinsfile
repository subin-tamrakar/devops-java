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
                echo 'Building'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing'
            }
        }
        stage('Archive') {
            steps {
                echo 'Archiving'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
}

