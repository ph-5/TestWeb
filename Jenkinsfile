@NonCPS
def getSendText() {
	return """
	`Name: ` *${currentBuild.fullDisplayName}*
	`Author: ` *${GIT_COMMITTER_EMAIL}*
	`Status: ` *${currentBuild.result}*
	`Duration: ` *${currentBuild.durationString}*
	`Commit: ` [${GIT_COMMITT_HASH}](${RUN_DISPLAY_URL})
	"""
}

pipeline {

	agent any

	stages {
		/* Initialize setting information */
		stage('Setting Info') {
			steps {
				script {
					env.GIT_COMMITTER_EMAIL = sh(
						script: "git --no-pager show -s --format='%ae' $GIT_COMMIT",
						returnStdout: true
					).trim()
					
					env.GIT_COMMITT_HASH = sh(
						script: "echo $GIT_COMMIT",
						returnStdout: true
					).trim().take(8)
				}
			}
		}

		/* Check the environment information  */
		stage('Info') {
			steps {
				sh 'dotnet --info'
				sh 'printenv'
			}
		}

		/* Configure */
		stage('Setting') {
			steps {
				sh 'echo '
			}
		}

		/* Dependencies */
		stage('Dependencies') {
			steps {
				sh 'echo '
			}
		}

		/* Build */
		stage('Build') {
			steps {
				sh 'dotnet restore'
				sh 'dotnet build'
			}
		}

		stage('Artifacts') {
			steps {
				echo 'Artifacts ...'
			}
		}

		stage('Deploy - QC') {
			steps {
				echo 'Deploing to QC ...'
			}
		}

		stage('Deploy - Prod') {
			steps {
				echo 'Deploing to Prod ...'
			}
		}
	}

	post {
		always {
			sh 'printenv'
		}

		success {
			telegramSend(message: getSendText(), chatId: env.telegramChatId)
		}

		failure {
			telegramSend(message: getSendText(), chatId: env.telegramChatId)
		}

		unstable {
			telegramSend(message: getSendText(), chatId: env.telegramChatId)
		}
	}
}