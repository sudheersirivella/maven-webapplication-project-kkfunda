pipeline 
{
  agent any
  tools
  {
    maven "maven-3.9.6"
  }


  stages
  {

    stage('git checkout')
    {
      steps
      {
      git branch: 'master', url: 'https://github.com/sudheersirivella/maven-webapplication-project-kkfunda'
      }
    }

    stage('COMPILE')
    {
      steps
      {
        sh "mvn compile"
      }
    }

   stage('Build')
    {
      steps
      {
        sh "mvn clean package"
      }
    }

    stage('SQ Report')
    {
      steps
      {
        sh "mvn sonar:sonar"
      }
    }


   stage('Articat Backup')
    {
      steps
      {
        sh "mvn deploy"
      }
    }

stage('Deploy To Tomcat')
    {
      steps
      {
        sh """
      curl -u admin:admin \
--upload-file /var/lib/jenkins/workspace/MBPL_JIOPROJECT_BY_SUDHEER/target/maven-web-application.war \
"http://13.233.104.217:8080/manager/text/deploy?path=/maven-web-application&update=true"
        """  
      }
    }


   


  } //stages ending
    
} //pipeline ending
