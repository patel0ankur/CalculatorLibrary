pipeline {
  agent any
  environment {
        // BUILDDATE = currentDate.format("yyyy-MM-dd")
        //def jobBaseName = "${env.JOB_NAME}".split('/').last()
        GIT_TAG = "$JOB_NAME-$GIT_BRANCH-$BUILD_TIMESTAMP-$BUILD_NUMBER"
                
    }
  
  
  stages {
  
    

    stage('Cloning Git') {
      steps {
        git credentialsId: 'GitHub', url: 'https://github.com/patel0ankur/CalculatorLibrary.git'
	    //sh('git tag -f -a ${GIT_TAG} -m "tagging"')
	    //withCredentials([usernamePassword(credentialsId: 'GitHub', passwordVariable: 'pass', usernameVariable: 'user')]) {
           //sh('git push origin ${GIT_TAG}') 
//}
	    //sh('git tag ${BUILD_TAG}') 
            //sh('git push origin ${BUILD_TAG}')   
              
      }
    }
    stage('Tagging') {
            steps {
		 echo "Tagging: ${GIT_TAG}"  
		echo "BUILD_NUMBER :: ${BUILD_NUMBER}"
echo "BUILD_ID :: ${BUILD_ID}"
echo "BUILD_DISPLAY_NAME :: ${BUILD_DISPLAY_NAME}"
echo "JOB_NAME :: ${JOB_NAME}"
echo "JOB_BASE_NAME :: ${JOB_BASE_NAME}"
echo "BUILD_TAG :: ${BUILD_TAG}"
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
