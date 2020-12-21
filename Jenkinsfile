pipeline {
  agent any
  environment {
        def BUILDDATE = sh(script: "echo `date +%s`", returnStdout: true).trim()
        def jobBaseName = "${env.JOB_NAME}".split('/').last()
        GIT_TAG = "$jobBaseName-$BUILDDATE-$BUILD_NUMBER"
                
    }
  
  
  stages {
  
    stage('Tagging') {
            steps {
			 sh('git tag -a ${GIT_TAG}' -m "Tagging the file")
			 sh('git push --tags') 
			  
              echo "Tagging: ${GIT_TAG}"
                }
            }

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
