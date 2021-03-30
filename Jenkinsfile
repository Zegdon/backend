
//SCRIPTED




//DECLARATIVE

pipeline {
       agent any

      environment{
      registry = "csabaazari/"
      dockerHome = tool 'myDocker'
      registryCredential = 'dockerlogin'
      mavenHome = tool 'myMaven'
      PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"

      }



        stages {
            stage('Checkout') {
                steps {
                       sh 'mvn --version'
                       sh 'docker --version'

                      echo "Build"
                      echo "PATH - $PATH"
                      echo "BUILD_NUMBER - $env.BUILD_NUMBER"
                      echo "BUILD_ID - $env.BUILD_ID"
                      echo "JOB_NAME - $env.JOB_NAME"
                      echo "BUILD_TAG - $env.BUILD_TAG"
                      echo "BUILD_URL - $env.BUILD_URL"
                }
            }


						stage('Package'){
                            steps {
                                sh "mvn clean package"
                             }

                        }

                        stage('Docker Compose Build') {
                            steps {
                            sh "docker-compose build"
                            }

                        }
                  stage('Docker push image') {
                  docker.Registry('https://hub.docker.com/', 'dockerlogin') {
                    sh "docker push csabaazari/user-service:latest"
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

