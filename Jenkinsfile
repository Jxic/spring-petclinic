pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './mvnw package'
      }
    }

    stage('SonarQube Analysis') {
      steps {
        withSonarQubeEnv('petclinic') {
          sh './mvnw clean verify sonar:sonar -Dsonar.projectKey=petclinic1'
        }

        waitForQualityGate true
      }
    }

    stage('Save Artifact') {
      steps {
        archiveArtifacts 'target/*.jar'
      }
    }

  }
}