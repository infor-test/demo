pipeline {
    agent { label 'demo'
	}
options {
//timestamps()
    buildDiscarder(logRotator(numToKeepStr: '4'))
  }
environment {
  kishore = "*********************-${BUILD_NUMBER}************************"
  BUILD_VERSION = "MXL-${BUILD_NUMBER}"
  }
	parameters {
            string(name: 'please enter your name', defaultValue: 'asdfasdf', description: 'this is test exmple')
	    string(name: 'Environment', defaultValue: '', description: 'adfad')
}
       stages {
		 stage('Build name') {
                    steps {
                        script {
                         currentBuild.displayName = env.kishore
                       }
		    }
		}
	    stage ('1') {
		   steps {
		      git credentialsId: '3d544f37-c71f-4f0f-9e84-c60e24f53cce', url: 'https://github.com/infor-test/demo.git'
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
			    
            }
          }
	}
	post {
		always {
			 deleteDir()
		}
	}
}
