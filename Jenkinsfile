pipeline {
    agent any 
	stages {
		
		stage('Skip the build'){
			steps {
				scmSkip(deleteBuild: false, skipPattern:'.*\\[ci skip\\].*')
			}
		}
        stage('Static Analysis') {
            steps {
                echo 'Run the static analysis to the code' 
            }
        }
        stage('Compile') {
            steps {
                echo 'Compile the source code' 
            }
        }
        stage('Security Check') {
            steps {
                echo 'Run the security check against the application' 
            }
        }
        stage('Run Unit Tests') {
            steps {
                echo 'Run unit tests from the source code' 
            }
        }
        stage('Run Integration Tests') {
            steps {
				script{
					echo 'Run only crucial integration tests from the source code' 
					sh "git status"
				}
                
            }
        }
        stage('Publish Artifacts') {
            steps {
                script {
					echo 'Save the assemblies generated from the compilation' 
					def gitCreds = "${env.GITCRED}"
					//sshagent (credentials : ["${gitCreds}"]) {
					//	ssh "git commit -m '[ci skip] Upversion Build"
					//	ssh "git push"
					}
				}
            }
        }
			
    }
	
}