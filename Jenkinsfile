def testfunction() {
		echo "@@@@@@@@@@%%%%%%%%%%%%%%%%"
	} // function end
def emailBuildIssue(buildResult, mailTo) {

    if ("${buildResult}" == "FAIL") {
        emailext (
            to: "${mailTo}",
            attachLog: true,
            subject: "${DEFAULT_SUBJECT} ${buildResult}",
            body: """<p> ${DEFAULT_BUILD_CONTENT} : ${BUILD_NUMBER} </p>
                     <p> Jenkins Job: ${BUILD_URL}""",
            mimeType: 'text/html',
        )
    } else {
        emailext (
            to: "${mailTo}",
            subject: "${DEFAULT_SUBJECT} ${buildResult}",
            body: """<p> ${DEFAULT_BUILD_CONTENT} : ${BUILD_NUMBER} </p>
                     <p> Jenkins Job: ${BUILD_URL}""",
            mimeType: 'text/html',
        )
    }
}
pipeline {
	
   // agent { label 'demo'
	agent any
	//}
options {
timestamps()
    buildDiscarder(logRotator(numToKeepStr: '4'))
  }
environment {
  kishore = "Test-${BUILD_NUMBER}"
  myname = "apple"
  BUILD_VERSION = "MXL-${BUILD_NUMBER}"
	DEFAULT_SUBJECT = "*************************"
	DEFAULT_BUILD_CONTENT = "&&&&&&&&&&&&&&&&&&&&&&&&&&"
  }
	/*parameters {
            string(name: 'please enter your name', defaultValue: 'asdfasdf', description: 'this is test exmple')
	    string(name: 'Environment', defaultValue: '', description: 'adfad')
}*/
	triggers {
     upstream(upstreamProjects: 'test', threshold: hudson.model.Result.SUCCESS) 
 }
       stages {
		 stage('Build name') {
                    steps {
                        script {
                         currentBuild.displayName = env.kishore
                       }
		    }
		}
	    stage ('scm checkout') {
		   steps {
		      git branch: 'master', credentialsId: 'e24932a1-95ce-48d5-8787-56d43a0f2bab', url: 'https://github.com/infor-test/adtra-project.git'
		   }
		}
		stage ('2') {
		    steps {
			    echo "hello welcome"
				}
		}
		stage ('file-download') {
			steps {
				script {
				//sh 'wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.68/bin/apache-tomcat-9.0.68.tar.gz'
					echo "welcome"
					}
			     }
		}
		stage('Example') {
                    steps {
                        echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
			    echo "My job name is ${env.JOB_NAME}"
			    echo "++++++++++++++++-${env.BUILD_TAG}"
			    echo ">>>>>>>>>>>>>>>>-${env.BUILD_URL}"
			    echo "#################-${env.EXECUTOR_NUMBER}"
			    echo "@@@@@@@@@@@@@@@@@-${env.JAVA_HOME}"
			    echo "!!!!!!!!!!!!!!!!!-${env.NODE_NAME}"
			    echo "&&&&&&&&&&&&&&&&&&-${env.NODE_NAME}"
			    echo "${myname}"
            }
          }
	       stage ('Trigger downstream job') {
		       steps {
			       echo "triggering downstream job.........."
			       //build 'test'
			        echo "${myname}"
		       }
	       }
	       stage ('call function') {
		       steps {
		       testfunction()
		       }
	       }
	} // end of stages
	post {
		always {
			 deleteDir()
			failure {
			 emailBuildIssue('FAIL', 'kishore.t533@gmail.com')
			}
		}
	}
} // end of pipeline 
