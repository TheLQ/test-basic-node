pipeline {
	agent { docker { image 'node:7-alpine' } }

	environment {
		WIN_LINUX  = "brailleblaster-daily-linux.zip"
        OTHER_var = "asdf"
    }

    stages {
        stage("first") {
            steps {
                sh "node --version"
            }
        }
    }
}
