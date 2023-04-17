pipeline {
  agent any
  
  stages {
    stage('checkout') {
      steps{
       git https://github.com/venddy/jenkins_file/edit/master/Jenkinsfile
      }
    }
  
  stage('Build'){
    steps{
            bat 'mvn clean install'
    }
    
  }
  stage('test'){
    steps{
        bat 'mvn test'
    }
  }
  }
}
}
