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
     // def mvnHome =  tool name: 'maven-3', type: 'maven'   
     // sh "${mvnHome}/bin/mvn package"
   }
   stage('Email Notification'){
      mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      Thanks
      Hari''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'hari.kammana@gmail.com'
   }
   stage('Slack Notification'){
       slackSend baseUrl: 'https://hooks.slack.com/services/',
       channel: '#jenkins-pipeline-demo',
       color: 'good', 
       message: 'Welcome to Jenkins, Slack!', 
       teamDomain: 'javahomecloud',
       tokenCredentialId: 'slack-demo'
   }
}
