node('master')

{

    stage('ContinuousDownload-Loans') 
    {
	git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('ContinuousBuild-Loans') 
    {
        sh label: '', script: 'mvn package'   
    }
    stage('ContinuousDeploy-Loans') 
    {
    sh label: '', script: 'scp /home/ubuntu/.jenkins/workspace/scriptedpipeline/webapp/target/webapp.war ubuntu@172.31.1.213:/var/lib/tomcat8/webapps/testapp.war'   
    }
    stage('ContinuousTesting-Loans') 
    {
     git 'https://github.com/intelliqittrainings/FunctionalTesting.git' 
     
     sh label: '', script: 'java -jar /home/ubuntu/.jenkins/workspace/scriptedpipeline/testing.jar'
    }
}

