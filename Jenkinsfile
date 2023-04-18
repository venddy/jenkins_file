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
       bat 'mvm clean package'

    }
    
  }
 /* stage('test'){
    steps{
        bat 'mvn test'
    }
  }*/
  }
}
