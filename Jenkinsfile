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
       bat 'docker login -u venddy -p Venkata@970569'
       bat 'docker build -t venddy/mvnimage .'
       bat 'docker push venddy/mvnimage:latest'

      }
    }
  }
}
def getVersion(){
  def commitHASH = bat lable:'', returnStdout: true, script: 'git rev-parse --short HEAD'
}
