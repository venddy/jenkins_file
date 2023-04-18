pipeline {
  agent any
  tools {
  maven 'maven'
  }
environment {
  docker = "getVersion()"
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
    stage('Docker Build') {
    	
      steps {
        bat 'docker build . -t venddy/venkataimage:"${docker}" '
 
      }
    }
  }
}
def getVersion(){
  def commitHASH = bat lable:'', returnStdout: true, script: 'git rev-parse --short HEAD'
}
