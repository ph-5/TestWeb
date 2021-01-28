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
		/* 設定資訊 */
		stage('Setting Info') {
			steps {
				echo 'Setting Info ...'
			}
		}

		/* 顯示資訊 */
		stage('Info') {
			steps {
				echo 'Show Infomation ...'
			}
		}

		/* 建置前 */
		stage('Setting') {
			steps {
				echo 'Setting ...'
			}
		}

		/* 相依 */
		stage('Dependencies') {
			steps {
				echo 'Dependencies ...'
			}
		}

		/* 建置 */
		stage('Build') {
			steps {
				echo 'Buliding ...'
			}
		}

		/* 打包 */
		stage('Artifacts') {
			steps {
				echo 'Artifacts ...'
			}
		}

		/* 發佈 - QC */
		stage('Deploy - QC') {
			steps {
				echo 'Deploing to QC ...'
			}
		}

		/* 發佈 - Prod */
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