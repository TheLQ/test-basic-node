pipeline {
	agent any

	environment {
		JRE_32_DIR  = credentials('JRE_32_DIR')
		JRE_64_DIR  = credentials('JRE_64_DIR')
		WIN_LINUX  = "brailleblaster-daily-linux.zip"
    }

    stages {
        stage("first") {
            sh "env"
        }
    }
}
