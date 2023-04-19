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
        withCredentials([string(credentialsId: 'venddy', variable: 'dockervariable')]) {
          bat 'docker login -u venddy -p %dockervariable%'
    
}
       bat 'docker build -t venddy/mvnimage .'
       bat 'docker push venddy/mvnimage:latest'

      }
    }
    stage ("deploy"){
      steps{ 
        ansiblePlaybook credentialsId: 'Ansible', disableHostKeyChecking: true, installation: 'Ansible', inventory: 'Inventoryfile', playbook: 'ansible-yml.yml', executable: '/usr/bin/ansible-playbook'
      }
    } 
  }
}
def getVersion(){
  def commitHASH = bat lable:'', returnStdout: true, script: 'git rev-parse --short HEAD'
}
