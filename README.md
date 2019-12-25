pipeline{
  agent any
  environment{
  PATH = "${PATH}:${tool name: 'maven3', type: 'maven'}/bin"
  stages{
      stage('SCM Checkout'){
	  steps {
	  git credentialsId: 'github', url: 'https://github.com/javahometech/6pmwebapp' 
	  }
	  }
	  stage ('Maven Build'){
	  steps{
	  script{
	  def mvnHome = tool name: 'maven3', type:'maven'
	  sh script:"${mvnHome}/bin/mvn clean package"
	  }
	  }
	  }
	  }
	  }
