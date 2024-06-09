pipeline {
  agent any
  tools {
  maven 'Maven 3.9.6'
  stages{
      stage("build"){
          steps{
              echo 'complilation in process...'
              sh 'mvn compile'
          }
      }
      stage("test"){
          steps{
              echo 'testing in progress'
              sh 'mvn clean test'
          }
      }
      stage("package"){
          steps{
              echo 'packaging the bundle'
              sh 'mvn package -DskipTests'
          }
      }
  }

  post{
    always{
        echo 'This pipeline is completed..'
    }
  }
}
