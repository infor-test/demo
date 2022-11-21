def testfunction() {
		echo "@@@@@@@@@@%%%%%%%%%%%%%%%%"
	} // function end
pipeline {
	
   // agent { label 'demo'
	agent any
	//}
options {
timestamps()
    buildDiscarder(logRotator(numToKeepStr: '4'))
  }
environment {
  kishore = "*********************-${BUILD_NUMBER}************************"
  myname = "apple"
  BUILD_VERSION = "MXL-${BUILD_NUMBER}"
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
	/*post {
		always {
			 deleteDir()
		}
	} */
} // end of pipeline 
