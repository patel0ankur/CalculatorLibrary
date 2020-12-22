pipeline {
  agent any
  environment {
        def BUILDDATE = sh(script: "echo `date +%s`", returnStdout: true).trim()
        def jobBaseName = "${env.JOB_NAME}".split('/').last()
        GIT_TAG = "$jobBaseName-$BUILDDATE-$BUILD_NUMBER"
                
    }
  
  
  stages {
  
    

    stage('Cloning Git') {
      steps {
        git credentialsId: 'GitHub', url: 'https://github.com/patel0ankur/CalculatorLibrary.git'
	    sh('git tag -a ${GIT_TAG} -m "tagging"')
            sh('git push origin ${GIT_TAG}')   
              
      }
    }
    stage('Tagging') {
            steps {
		 echo "Tagging: ${GIT_TAG}"   
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
