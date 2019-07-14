node {
   stage('init') {
    checkout scm
	}
	  stage('build') {
	   sh '''
	   apt-get update && apt-get install zip
	   mvn clean package -DskipTests
	   cd target
	   cp ../src/main/resources/web.config web.config
       cp jb-hello-world-maven-0.1.0.jar app.jar
	   zip -r todo.zip app.jar web.config
	   '''
	}
	stage('deploy') {
	azureWebAppPublish azureCredentialsId: env.AZURE_CRED_ID,
	resourceGroup: env.RES_GROUP, appName: env.WEB_APP, filePath: "**/todo.zip"
	}
}