pipeline {
    agent any
    stages {
        stage('Pull Code from branch') {
            steps {
		    deleteDir()
                  git branch: 'main', credentialsId: 'srsave', url: 'https://github.com/srsave/AspWithNUnit.git'
		    sh 'git log --oneline -1 ${GIT_COMMIT}'
            }
	}
    }
}
