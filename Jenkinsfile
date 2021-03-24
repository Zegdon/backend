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
	  jdkHome = tool 'myJdk'
      PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	//  PATH = "$dockerHome/bin:$jdkHome/bin:$PATH"
	  

      }



        stages {
            stage('Checkout') {
                steps {
                       sh 'mvn --version'
                       sh 'docker --version'
					   sh 'java -version'

                      echo "Build"
                      echo "PATH - $PATH"
                      echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                      echo "BUILD_ID - $env.BUILD_ID"
                      echo "JOB_NAME - $env.JOB_NAME"
                      echo "BUILD_TAG - $env.BUILD_TAG"
                      echo "BUILD_URL - $env.BUILD_URL"
                }
            }

                    //    stage('Compile'){
                      //      steps {
                       //         sh "mvn clean compile"


                         //   }
//
//
                      //  }
						stage('Package'){
                            steps {
                                sh "mvn clean package"


                            }


                        }
                 
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

