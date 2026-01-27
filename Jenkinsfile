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
                sh 'java --version'
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
                archiveArtifacts artifacts: "build/libs/**/*.jar", fingerprint: true
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying'
            }
        }
    }
    post {
        success {
            script {
                def subject = "${env.JOB_NAME} #${env.BUILD_NUMBER} SUCCESS"
                def body = """\
Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: SUCCESS
Build URL: ${env.BUILD_URL}"""
                mail(
                    to: 'work.subin.tamrakar@gmail.com',
                    subject: subject,
                    body: body
                )
            }
        }
        failure {
            script {
                def subject = "${env.JOB_NAME} #${env.BUILD_NUMBER} FAILURE"
                def body = """\
Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: FAILURE
Build URL: ${env.BUILD_URL}"""
                mail(
                    to: 'work.subin.tamrakar@gmail.com',
                    subject: subject,
                    body: body
                )
            }
        }
        unstable {
            script {
                def subject = "${env.JOB_NAME} #${env.BUILD_NUMBER} UNSTABLE"
                def body = """\
Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: UNSTABLE
Build URL: ${env.BUILD_URL}"""
                mail(
                    to: 'work.subin.tamrakar@gmail.com',
                    subject: subject,
                    body: body
                )
            }
        }
        aborted {
            script {
                def subject = "${env.JOB_NAME} #${env.BUILD_NUMBER} ABORTED"
                def body = """\
Job Name: ${env.JOB_NAME}
Build Number: ${env.BUILD_NUMBER}
Status: ABORTED
Build URL: ${env.BUILD_URL}"""
                mail(
                    to: 'work.subin.tamrakar@gmail.com',
                    subject: subject,
                    body: body
                )
            }
        }
    }
}

