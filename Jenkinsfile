pipeline {
  agent any
  stages {

    stage('Cloning Git') {
      steps {
        git credentialsId: 'GitHub', url: 'https://github.com/patel0ankur/CalculatorLibrary.git'
      }
    }
    
    stage('Install Requirements'){
      steps {
        sh 'sudo pip3.6 install -r requirements.txt'
      }
    }

    stage('Unit Testing') {
      steps {
        sh 'python3 -m pytest -v --cov=calculator'
      }   
    }

    stage('Run Python Script') {
      steps {
        sh 'sudo python3 calculator.py'
      }   
    }

  }
}