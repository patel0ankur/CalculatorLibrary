pipeline {
  agent any
  environment {
        // BUILDDATE = currentDate.format("yyyy-MM-dd")
        //def jobBaseName = "${env.JOB_NAME}".split('/').last()
        GIT_TAG = "$JOB_NAME-$BUILD_TIMESTAMP-$BUILD_NUMBER"
                
    }
  
  stages {

    stage('Cloning Git') {
      steps {
	    sh('git tag -f -a ${GIT_TAG} -m "tagging"')
	    withCredentials([usernamePassword(credentialsId: 'GitHub', passwordVariable: 'pass', usernameVariable: 'user')]) {
		   sh('git tag -f -a ${GIT_TAG} -m "tagging"')
           sh('git push origin ${GIT_TAG}') 
		  }
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
	  
  }
}
