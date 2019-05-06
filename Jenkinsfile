pipeline {
    agent { docker { image 'node:6.3' } }
	environment{
		VAR_1 = 'my_var_1'
		VAR_2 = 'my_var_2'
	}
    stages {
		stage('print var'){
			steps{
				sh 'printenv'
			}
		}
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
		stage('some times'){
			steps {
				timeout(time: 1, unit: 'MINUTES') {
					sh 'echo "Hi :-)"'
				}
			}
		}
    }
	post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}