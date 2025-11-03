pipeline {
  agent { docker { image 'maven:3.9.8-eclipse-temurin-17' } }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
        sh 'echo "Current directory:" && pwd && ls -la'
      }
    }

    stage('Build') {
      steps {
        sh 'mvn -B clean package -DskipTests'
      }
    }

    stage('Test') {
      steps {
        sh 'mvn test -q'
      }
    }

    stage('Archive JAR') {
      steps {
        archiveArtifacts artifacts: 'target/*.jar', fingerprint: true
      }
    }
  }

  post {
    success { echo 'Build succeeded' }
    failure { echo 'Build failed' }
  }
}
