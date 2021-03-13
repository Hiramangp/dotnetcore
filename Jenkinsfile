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
	    stage('Code Inspect'){
		steps {    
       		echo 'Now performing code Analysis'
		bat label: 'code-Analysis-Step1', script: '"C:\\soft\\sonar-scanner-msbuild-5.1.0.28487-net46\\SonarScanner.MSBuild.exe" begin /k:"AspWithNUnit"'
		bat label: 'code-Analysis-Step2', script: '"C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Community\\MSBuild\\Current\\Bin\\MSBuild.exe" C:\\Users\\Administrator\\.jenkins\\workspace\\test2\\AspWithNUnit.sln /t:Rebuild'
		bat label: 'code-Analysis-Step3', script: '"C:\\soft\\sonar-scanner-msbuild-5.1.0.28487-net46\\SonarScanner.MSBuild.exe" end'
      		println 'Success'
		}
    	}
	    stage('FTA Testing'){
		steps {   
        	echo 'Now performing Nunit'
       		build 'FTA'
       		println 'Success'
		}
    	}
	    stage('Nuint  Testing'){
		steps {  
    		echo 'Now performing FTA'		
    		build 'Nunit'		
    		println 'Success'
		}
   	 }
	    
    }
}
