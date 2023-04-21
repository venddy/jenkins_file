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
       sh 'mvn clean package'

    }
    
  }
  stage('test'){
    steps{
        sh 'mvn test'
    }
  }
    stage('Docker Build') {
    	
      steps {
        withCredentials([string(credentialsId: 'venddy', variable: 'dockervariable')]) {
          sh 'docker login -u venddy -p %dockervariable%'
    
}
       sh 'docker build -t venddy/mvnimage .'
       sh 'docker push venddy/mvnimage:latest'

      }
    }
    stage ("deploy"){
      steps{ 
        ansiblePlaybook credentialsId: 'Ansible', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'Inventoryfile', playbook: '/cygwin64/home/sree/ansible-yml.yml'
      }
    } 
  }
}
def getVersion(){
  def commitHASH = sh lable:'', returnStdout: true, script: 'git rev-parse --short HEAD'
}
