node {
   stage('init') {
    checkout scm
	}
	  stage('build') {
	   sh '''
	   mvn clean package -DskipTests
	   cd target
	   cp gs-spring-boot-0.1.0.jar app.jar
	   zip hello-world.zip app.jar
								        '''
	}
	stage('deploy') {
	azureWebAppPublish azureCredentialsId: env.AZURE_CRED_ID,
	resourceGroup: env.RES_GROUP, appName: env.WEB_APP, filePath: "**/todo.zip"
	}
}
