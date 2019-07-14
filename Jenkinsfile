node {
   stage('init') {
    checkout scm
	}
	  stage('build') {
	   sh '''
	   mvn clean package -DskipTests
	   cd target
	   zip hello-world.zip hello-world-maven-0.1.0-shaded.jar
	   '''
	}
	stage('deploy') {
	azureWebAppPublish azureCredentialsId: env.AZURE_CRED_ID,
	resourceGroup: env.RES_GROUP, appName: env.WEB_APP, filePath: "**/hello-world.zip"
	}
}
