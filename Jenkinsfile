pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './mvnw package'
      }
    }

    stage('SonarQube Analysis') {
      withSonarQubeEnv() {
        sh "./mvnw clean verify sonar:sonar -Dsonar.projectKey=petclinic1"
      }
    }
  }
  
}