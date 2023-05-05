pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'compile maven app'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'test maven app'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'package maven app'
        sh 'mvn package -DskipTests'
      }
    }

    stage('artifactarchive') {
      steps {
        archiveArtifacts 'target/*.war'
      }
    }

    stage('email') {
      steps {
        emailext(subject: 'test email', body: 'complete', from: 'nayankankaria@gmail.com', to: 'nayankankaria@gmail.com')
      }
    }

  }
  tools {
    maven 'Maven 3.6.3'
  }
}