node {
    
	

    env.AWS_ECR_LOGIN=true
    def newApp
    def registry = 'https://cloud.docker.com/u/dineshpsingh/repository/docker/'
	def imageName = 'dineshpsingh/docker-test'
    def registryCredential = 'dockerhub'
	
	stage('Git') {
		git 'https://github.com/dineshpsingh16/node-todo-frontend'
	}
	stage('Build') {
		sh 'npm install'
	}
	stage('Test') {
		sh 'npm test'
	}
	stage('Building image') {
        docker.withRegistry(  registry, registryCredential ) {
		    def buildName = imageName + ":$BUILD_NUMBER"
			newApp = docker.build buildName
			newApp.push()
        }
	}

    stage('Removing image') {
        sh "docker rmi $registry:$BUILD_NUMBER"
        sh "docker rmi $registry:latest"
    }
    
}
