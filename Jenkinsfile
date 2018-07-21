node{
	stage('Checkout'){
		//Checkout Git repo
		//git repo:'https://github.com/ksubbarao/Beach-resort.git', branch:'master'
		checkout scm
	}
	
	stage('Build Automation'){
		def mvnHome = tool 'Maven-3.5.4'
		mvnHome = mvnHome + '\\bin'
		def winJDK = tool 'JDK-1.3.1'
		println mvnHome
		withEnv(["MAVEN_HOME=${mvnHome}", "JAVA_HOME=${winJDK}"]){
			bat "${mvnHome}\\mvn clean package"
		}
	}
}
