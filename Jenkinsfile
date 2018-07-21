node{
	stage('Checkout'){
		//Checkout Git repo
		//git repo:'https://github.com/ksubbarao/Beach-resort.git', branch:'master'
		checkout scm
	}
	
	stage('Build Automation'){
		def mvnHome = tool 'Maven-3.5.4'
		println mvnHome
	}
	
}
