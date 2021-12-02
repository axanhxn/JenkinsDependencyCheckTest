pipeline {
	agent any
	stages {
		stage('Checkout SCM') {
			steps {
				git 'JenkinsDependencyCheckTest',
                credentialsId='79f3bc7e-7a30-4192-a4ca-759734d69645'
			}
		}

		stage('OWASP DependencyCheck') {
			steps {
				dependencyCheck additionalArguments: '--format HTML --format XML', odcInstallation: 'Default'
			}
		}
	}	
	post {
		success {
			dependencyCheckPublisher pattern: 'dependency-check-report.xml'
		}
	}
}