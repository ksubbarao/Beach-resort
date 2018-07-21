node{
	
	def mvnHome = tool 'Maven-3.5.4'
	mvnHome = mvnHome + '\\bin'
	def winJDK = tool 'JDK-1.3.1'
	println mvnHome
	
	env.versionNumber = '1.0.0.' + BUILD_NUMBER
	def server = Artifactory.server 'local_Artifactory'
	
	stage('Checkout'){
		//Checkout Git repo
		//git repo:'https://github.com/ksubbarao/Beach-resort.git', branch:'master'
		checkout scm
	}
	
	stage('Code coverage and Analysis'){
		withEnv(["JAVA_HOME=${winJDK}"]){
			bat "${mvnHome}\\mvn sonar:sonar"
		}
	}
	
	stage('Build Automation'){
		
		withEnv(["JAVA_HOME=${winJDK}"]){
			bat "${mvnHome}\\mvn clean package"
		}
	}
	
	stage('Build Management'){
		def buildInfo = Artifactory.newBuildInfo()
		buildInfo.name = 'Beach'
		buildInfo.number = env.versionNumber
		
		def uploadSpec = """{
		"files": [
			{
			  "pattern": "target\\Beach.war",
			  "target": "maven-dev-local/WAR-Apps/Beach-Resort/${env.versionNumber}/"
			}
		 ]
		}"""
		
		//println pattern
		
		server.upload(uploadSpec)
		
		//server.upload spec: uploadSpec, buildInfo: buildInfo
		server.publishBuildInfo buildInfo
	}
}
