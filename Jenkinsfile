pipeline
{
    agent any
	tools
	{
	 jdk 'JAVA_HOME'
	 maven 'MAVEN_HOME'
	}
    stages
    {
        stage('ContDownload')
        {
            steps
            {
                checkout scm
            }
        }
        stage('ContBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContDeployment')
        {
            steps
            {
               sshPublisher(publishers: [sshPublisherDesc(configName: 'tomcat-server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: '/opt/apache-tomcat-8.5.43/bin/startup.sh', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '/opt/apache-tomcat-8.5.43/webapps', remoteDirectorySDF: false, removePrefix: '', sourceFiles: 'target/webapp.war')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }

        }
	    
	}
		
}
