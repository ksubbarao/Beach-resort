node{
	
	def mvnHome = tool 'Maven-3.5.4'
	mvnHome = mvnHome + '\\bin'
	def winJDK = tool 'JDK-1.3.1'
	println mvnHome
	
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
}
