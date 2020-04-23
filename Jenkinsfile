node('master')

{

    stage('ContinuousDownload') 
    
	{git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild') 
    {
    sh label: '', script: 'mvn package'   
    }
    stage('ContinuousDeploy') 
    {
    sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.1.213:/var/lib/tomcat8/webapps/testapp.war'   
    }
    stage('ContinuousTesting') 
    {
     git 'https://github.com/intelliqittrainings/FunctionalTesting.git' 
     
     sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline/testing.jar'
    }
    stage('ContinuousDelivery') 
    {
        sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.3.5:/var/lib/tomcat8/webapps/prodapp.war'
    }
}

