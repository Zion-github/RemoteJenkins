node('slave1') 
{
    stage ('ContinuousDownload')
{
    git 'https://github.com/intelliqittrainings/maven.git'
}
stage ('ContinuousBuild')
{
   sh 'mvn package' 
}
stage ('ContinuousDeployment')
{
 sh 'scp /home/ubuntu/.jenkins/workspace/ScriptPipeline/webapp/target/webapp.war ubuntu@10.3.0.138:/var/lib/tomcat9/webapps/testapp.war'
}
stage ('ContinuousTesting')
{
    git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
    sh 'java -jar /home/ubuntu/.jenkins/workspace/ScriptPipeline/testing.jar'
}
stage ('ContinuousDelivery')
{    
    sh 'scp /home/ubuntu/.jenkins/workspace/ScriptPipeline/webapp/target/webapp.war ubuntu@10.3.0.236:/var/lib/tomcat9/webapps/prodapp.war'
}
}

