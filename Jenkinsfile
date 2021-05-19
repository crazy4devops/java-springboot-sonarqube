pipeline {
      agent any
      stages {     
        stage("Build") {
            steps {
                //sh 'cd mvn clean package'
                sh '''
                  cd sonarqube-scanner-maven/maven-basic/
                  cd mvn clean package
                '''
            }
        }
        stage("SonarQube Analysis") {
            steps {
              sh 'mvn sonar:sonar'
              sh '''
                  cd sonarqube-scanner-maven/maven-basic/
                  mvn sonar:sonar
                '''
            }
        }
        stage('Approve Deployment') {
              input{
                   message "Do you want to proceed for deployment?"
                      }
              steps {
                  //Add deploy steps & Alerts below
                  sh 'echo "Deploying into Server"' 

                }
          } 
          
      } // stage
        
  // post {

  //     aborted {

  //       echo "Sending message to Slack"
  //       slackSend (color: "${env.SLACK_COLOR_WARNING}",
  //                 channel: "${params.SLACK_CHANNEL_2}",
  //                 message: "*ABORTED:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} by ${env.USER_ID}\n More info at: ${env.BUILD_URL}")
  //     } // aborted

  //     failure {

  //       echo "Sending message to Slack"
  //       slackSend (color: "${env.SLACK_COLOR_DANGER}",
  //                 channel: "${params.SLACK_CHANNEL_2}",
  //                 message: "*FAILED:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} by ${env.USER_ID}\n More info at: ${env.BUILD_URL}")
  //     } // failure

  //     success {
  //       echo "Sending message to Slack"
  //       slackSend (color: "${env.SLACK_COLOR_GOOD}",
  //                 channel: "${params.SLACK_CHANNEL_1}",
  //                 message: "*SUCCESS:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} by ${env.USER_ID}\n More info at: ${env.BUILD_URL}")
  //     } // success

  // } // post
        
        
}
