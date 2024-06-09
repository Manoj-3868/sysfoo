pipeline {
  agent any
  stages {
    stage('build') {
      steps {
        echo 'complilation in process...'
        sh 'mvn compile'
      }
    }

    stage('test') {
      steps {
        echo 'testing in progress'
        sh 'mvn clean test'
      }
    }

    stage('package') {
      steps {
        echo 'packaging the bundle'
        sh '''# Truncate the GIT_COMMIT to the first 7 characters
GIT_SHORT_COMMIT=$(echo $GIT_COMMIT | cut -c 1-7)
# Set the version using Maven
mvn versions:set -DnewVersion="$GIT_SHORT_COMMIT"
mvn versions:commit'''
        sh 'mvn package -DskipTests'
        archiveArtifacts '**/target/*.jar'
      }
    }

  }
  tools {
    maven 'Maven 3.9.6'
  }
  post {
    always {
      echo 'This pipeline is completed..'
    }

  }
}