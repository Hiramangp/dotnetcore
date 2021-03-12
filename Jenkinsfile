pipeline {   
    stages {
        stage('build') {
            steps {
                git branch: 'main', credentialsId: 'srsave', url: 'https://github.com/srsave/AspWithNUnit.git'
            }
        }
    }
}
