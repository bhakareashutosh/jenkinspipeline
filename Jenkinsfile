pipeline {
    agent any
    stages {
        stage ('SCM for Java Code') {
            steps{
                git credentialsId: 'f52176a1-c3c7-4208-9b4b-adba5fb3e0e4', url: 'https://github.com/ashutoshbhakare/simpleMavenJunit'
                echo 'Polling to Developers SCM'
            }
        }
        stage ('Maven Compile') {
            steps{
                sh '''mvn clean
mvn compile'''
            }
        }
        stage ('Testing Code') {
            steps {
                sh '''mvn test'''
                echo 'Testing complete with Junit on maven'

            }
        }
        stage ('Package') {
            steps {
            sh 'mvn package'   
            }
        }
        stage ('Publish Test results'){
            steps {
            junit 'target/surefire-reports/*.xml'
            }
        }
        stage ('Execute Jar'){
            steps{
                sh 'java -jar target/*.jar'
            }
        }
    }
}
yea
