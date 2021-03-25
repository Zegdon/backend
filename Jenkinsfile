 //SCRIPTED




//DECLARATIVE

pipeline {
       agent any
      // agent { docker { image 'maven:latest' }  }
      // agent { docker { image 'node:13.8' }  }
      environment{
      registry = "csabaazari/currency-exchange-devops11"
      dockerHome = tool 'myDocker'
      mavenHome = tool 'myMaven'
	//  jdkHome = tool 'myJdk'
      PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	//  PATH = "$dockerHome/bin:$jdkHome/bin:$PATH"
	  

      }

        stages {
            stage('Checkout') {
                steps {
                       sh 'mvn --version'
                       sh 'docker --version'
		       sh 'java -version'
			sh 'docker-compose --version'

                      echo "Build"
                      echo "PATH - $PATH"
                      echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                      echo "BUILD_ID - $env.BUILD_ID"
                      echo "JOB_NAME - $env.JOB_NAME"
                      echo "BUILD_TAG - $env.BUILD_TAG"
                      echo "BUILD_URL - $env.BUILD_URL"
		      echo "JAVA_HOME - $env.JAVA_HOME%"
	              echo "JRE_HOME - $env.JRE_HOME%"
		      echo "MAVEN_HOME- $env.MAVEN_HOME%"
			
			
                }
            }

                        stage('Mvn clean package'){
                            steps {
                                sh "mvn clean package"


                            }


                        }
			stage('Docker compose'){
                            steps {
                        sh "ls -la"	    
		//	sh "docker-compose –f build-compose.yml"
				    
			//sh " docker-compose -f ~/var/jenkins_home/workspace/docker-compose.yml"	    
			//	sh "docker-compose build"
			//	sh "docker-compose up"


                            }


                        }
//		stage ('Build docker image') {
//                            steps {
//                            //"docker build -t csabaazari/currency-exchange-devops:$env.BUILD_TAG"
//                            script {
//                               dockerImage = docker.build("csabaazari/currency-exchange-devops11:${env.BUILD_TAG}")
//
//                             //  dockerImage = docker.run ("csabaazari/currency-exchange-devops11:${env.BUILD_TAG}")
 //                               }
  //                          }
   //                     }
//		stage ('Run docker image') {
 //                           steps {
   //                         sh "docker run -d -p 8077:8000 csabaazari/currency-exchange-devops11:${env.BUILD_TAG}"
     //                       }
     //                   }
                 
      }
      post {
            always {
                echo 'Im awsome. I run always'
            }
            success {
                echo 'I run when you are succesful'
            }
            failure {
                 echo 'I run when you fail'
            }
      }

}

