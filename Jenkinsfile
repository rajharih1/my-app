node {
	stage('SCM checkout') {
        /* Let's make sure we have the repository cloned to our workspace */

        	git 'https://github.com/rajharih1/my-app'
    }
	
	stage('Compile-Package'){
      // Get maven home path
      		def mvnHome =  tool name: 'maven-3', type: 'maven'   
      		sh "${mvnHome}/bin/mvn package"
    }
	stage('Push Docker Image'){
        	withCredentials([string(credentialsId: 'docker-pwd', variable: 'docker-password')]) {
            		sh "docker login -u hubrajesh -p ${docker-password}"
        }
	sh 'docker push hubrajesh/my-app:1.0'
    }
}
