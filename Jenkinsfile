pipeline {
  agent any
  tools {
  maven 'Maven_Home'
}

  
  stages {
    stage('checkout') {
      steps{
       git "https://github.com/venddy/jenkins_file.git"
      }
    }
  
  stage('Build'){
    steps{
            bat 'C:\Users\sree\OneDrive\Documents\apache-maven-3.9.1\bin\mvn clean package'
    }
    
  }
 /* stage('test'){
    steps{
        bat 'mvn test'
    }
  }*/
  }
}
