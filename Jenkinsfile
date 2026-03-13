pipeline {
    agent any

    tools {
        maven "Maven3"
        jdk "JDK17"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'github-credentials',
                    url: 'https://github.com/mohdsadiq101/java-maven-jenkins-sample'
            }
        }

        stage('Build') {
            steps {
                bat 'mvn clean install -DskipTests'
            }
        }

        stage('Test') {
            steps {
                bat 'mvn test'
            }
        }

        stage('Package') {
            steps {
                bat 'mvn package'
            }
            post {
                success {
                    archiveArtifacts artifacts: 'target\\*.jar', fingerprint: true
                }
            }
        }
    }
}
