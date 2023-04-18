pipeline {
  agent any
  tools {
  maven 'maven'
  }

  
  stages {
    stage('checkout') {
      steps{
       git "https://github.com/venddy/jenkins_file.git"
      }
    }
  
  stage('Build'){
    steps{
       bat 'mvn clean package'

    }
    
  }
  stage('test'){
    steps{
        bat 'mvn test'
    }
  }
  }
}
