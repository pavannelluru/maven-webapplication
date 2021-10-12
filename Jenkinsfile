node
{
   def mvnHome=tool name: "maven3.8.3"   
stage('CheckoutCode')
{
git branch: 'development',
credentialsId: 'e3bc929e-2bbd-49d1-8208-32588318e1ce',
url: 'https://github.com/pavannelluru/maven-webapplication.git'
}
 stage('Build')
 {
  sh "${mvnHome}/bin/mvn clean package"
 }
  /* stage('ExecuteSonarQubeReport')
 {
  sh "${mvnHome}/bin/mvn sonar:sonar"
 }
  stage('UploadArtifactIntoNexus')
 {
  sh "${mvnHome}/bin/mvn deploy"
 }
 
  stage('DeployToTomcat')
 {
  
  sshagent(['c264b0cd-cb0a-4732-9cd4-604071dc6dec']) 
  {
    sh  "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@3.109.2.77:/opt/apache-tomcat-9.0.53/webapps/"
  }
  }*/
   stage('SendEmailNotification')
 {
    emailext body: '''Build is Completed.

    Regards,
    Pavan Nelluru''', subject: 'Build is Over', to: 'pavipavan862@gmail.com'
}
}
