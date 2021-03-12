pipeline {
    agent any
    stages {
        stage('build') {
            steps {
                git branch: 'main', credentialsId: 'srsave', url: 'https://github.com/srsave/AspWithNUnit.git'
            }
	}
	stage('Compilation') {
            steps {
                println "Now proceeding for source compilation using MSBuild executable"
		bat label: 'msbuild-step', script: '"C:\\Windows\\Microsoft.NET\\Framework\\v4.0.30319\\MSBuild.exe" AspWithNUnit.sln /p:Configuration=Release /p:AllowUntrustedCertificate=True /p:CreatePackageOnPublish=True'
		bat label: 'Publish', script: '"C:\\Windows\\Microsoft.NET\\Framework\\v4.0.30319\\MSBuild.exe" AspWithNUnit.sln /p:DeployOnBuild=true /p:PublishProfile=CustomProfile /property:WarningLevel=2;OutDir=%WORKSPACE%\\Publish'
            }
        }
    }
}
