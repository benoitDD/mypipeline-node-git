pipeline {
    agent { docker { image 'node:6.3' } }
    stages {
        stage('build') {
            steps {
                sh 'echo "Hello world"'
				sh '''
					echo "Multiline sh works too"
					node --version
				'''
            }
        }
		stage('deploy') {
			steps {
				retry(3) {
					sh 'echo "Work forever"'
				}
			}
		}
    }
}