node{
   stage('SCM Checkout'){
     git 'https://github.com/aparnatechm/my-app'
      echo 'checkout success'
   }
   stage('Compile-Package-build'){
      // Get maven home path
      sh 'mvn clean package'
      echo 'rename war file'
      sh 'mv target/myweb*.war target/myweb.war'
      echo 'rename war file success'
      //kartik
     // def mvnHome =  tool name: 'maven-3', type: 'maven'   
     // kartik
     // sh "${mvnHome}/bin/mvn package"
   }
    stage('Deploy to Tomcat'){
      
      sshagent(['tomcatdev']) {
         sh 'scp -o StrictHostKeyChecking=no target/*.war ec2-user@172.31.24.211:/home/ec2-user/opt/tomcat8/webapps/'
         echo 'deploy to tomcat success'
      }
       echo 'deploy to tomcat success'
   }
   //stage('Email Notification'){
     // mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      //Thanks
      //Hari''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'hari.kammana@gmail.com'
  // }
   //stage('Slack Notification'){
       //slackSend baseUrl: 'https://hooks.slack.com/services/',
       //channel: '#jenkins-pipeline-demo',
       //color: 'good', 
       //message: 'Welcome to Jenkins, Slack!', 
       //teamDomain: 'javahomecloud',
       //tokenCredentialId: 'slack-demo'
   //}
}
