pipeline {
  agent any
  environment {
        // BUILDDATE = currentDate.format("yyyy-MM-dd")
        //def jobBaseName = "${env.JOB_NAME}".split('/').last()
        GIT_TAG = "$JOB_NAME-$BUILD_TIMESTAMP-$BUILD_NUMBER"
	def repositoryUrl = scm.getUserRemoteConfigs()[0].getUrl() 
                
    }
  
  stages {

    stage('Cloning Git') {
      steps {
<<<<<<< Updated upstream
	    //sh('git tag -f -a ${GIT_TAG} -m "tagging"')
	    sshagent(['Jenkins_server1']) {
    		   sh('git tag -f -a ${GIT_TAG} -m "tagging"')
		   sh('git tag -l')
		   sh('git push -f origin ${GIT_TAG}') 
		    //sh('git push http://${pass}:${user}@${repositoryUrl} refs/tags/${GIT_TAG}')
}
	    //withCredentials([usernamePassword(credentialsId: 'GitHub', passwordVariable: 'pass', usernameVariable: 'user')]) {

		//  }
=======
	    sh('git tag -f -a ${GIT_TAG} -m "tagging"')
	    withCredentials([usernamePassword(credentialsId: 'GitHub', passwordVariable: 'pass', usernameVariable: 'user')]) {
		   sh('git tag -f -a ${GIT_TAG} -m "tagging"')
           sh('git push origin ${GIT_TAG}') 
		  }
>>>>>>> Stashed changes
      }
    }
    stage('Tagging') {
            steps {
<<<<<<< Updated upstream
		   // giturl_push = ${GIT_URL}.split("//")[1]
		   // echo "Git UrL: ${giturl_push}"
		    echo scm.getUserRemoteConfigs()[0].getUrl()
		    echo "Tagging: ${GIT_TAG}"  
		    echo "BUILD_NUMBER :: ${BUILD_NUMBER}"
=======
		           echo "Tagging: ${GIT_TAG}"  
		           echo "BUILD_NUMBER :: ${BUILD_NUMBER}"
>>>>>>> Stashed changes
                   echo "BUILD_ID :: ${BUILD_ID}"
                   echo "BUILD_DISPLAY_NAME :: ${BUILD_DISPLAY_NAME}"
                   echo "JOB_NAME :: ${JOB_NAME}"
                   echo "JOB_BASE_NAME :: ${JOB_BASE_NAME}"
                   echo "BUILD_TAG :: ${BUILD_TAG}"
                }
            }
	  
  }
}
