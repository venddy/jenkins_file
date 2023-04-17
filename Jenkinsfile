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
            bat 'C:\Users\sree\OneDrive\Documents\maven\apache-maven-3.9.1\apache-maven\src\bin\mvn clean package'
    }
    
  }
 /* stage('test'){
    steps{
        bat 'mvn test'
    }
  }*/
  }
}
