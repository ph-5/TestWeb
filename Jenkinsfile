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
		/* �]�w��T */
		stage('Setting Info') {
			steps {
				echo 'Setting Info ...'
			}
		}

		/* ��ܸ�T */
		stage('Info') {
			steps {
				echo 'Show Infomation ...'
			}
		}

		/* �ظm�e */
		stage('Setting') {
			steps {
				echo 'Setting ...'
			}
		}

		/* �ۨ� */
		stage('Dependencies') {
			steps {
				echo 'Dependencies ...'
			}
		}

		/* �ظm */
		stage('Build') {
			steps {
				echo 'Buliding ...'
			}
		}

		/* ���] */
		stage('Artifacts') {
			steps {
				echo 'Artifacts ...'
			}
		}

		/* �o�G - QC */
		stage('Deploy - QC') {
			steps {
				echo 'Deploing to QC ...'
			}
		}

		/* �o�G - Prod */
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