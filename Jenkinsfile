pipeline {
    agent any
    stages {
        stage('Pull Code from branch') {
            steps {
		    deleteDir()
		     print 'hi'
                  git branch: 'main', credentialsId: 'hp', url: 'https://github.com/Hiramangp/dotnetcore.git'
		   // sh 'git log --oneline -1 ${GIT_COMMIT}' 
		      def commitMessages = ${GIT_COMMIT}
		    print 'hi'
            }
	}
    }
}
