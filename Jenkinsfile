pipeline {
    agent any

    options {
        skipDefaultCheckout()
    }
    
    tools {
        maven 'maven3'
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/lesypoo/gs-lesy-poo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        stage('Deploy to Nexus') {
            steps {
                withMaven(maven: 'maven3') {
                    sh 'mvn deploy -DskipTests'
        }
    }

    post {
        success {
            archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
        }
    }
}
