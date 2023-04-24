def call(Map config) {
 	
	
    pipeline{

        agent any
        tools {

maven 'maven'
jdk 'jdk8'

}
      
        stages{
            stage('Checkout'){
                steps{
                   script{
                      branch=config.branch
                      if(config.branch_pipe_value?.trim()){
							branch=config.branch_pipe_value
						  }
                      git credentialsId: 'bitbucket_id', url: "${config.url}", branch: "${branch}"
                    }
                }
            }
        
stage('tool initilization'){
steps {
sh "mvn --version"
sh "java -version"
}


}

stage('testing and packaging of the code'){

steps{

sh "mvn clean install"

}

}
}
}
}
