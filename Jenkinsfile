pipeline {
  agent {
    kubernetes {
        defaultContainer 'jnlp'
      yaml """
apiVersion: v1
kind: Pod
metadata:
  labels:
    some-label: some-label-value
spec:
  containers:
  - name: maven
    image: maven:alpine
  - name: node
    image: node:8-alpine
"""

    }
  }
  environment {
    CONTAINER_ENV_VAR = 'container-env-var-value'
  }
  stages {
    stage('Run maven') {
      steps {
        sh 'set'
        // sh 'test -f /usr/bin/mvn' // checking backwards compatibility
        sh "echo OUTSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}"
        container('maven') {
          sh 'echo INSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          sh 'mvn -version'
        }
        container('node') {
          sh 'echo INSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          sh 'node --version'
        }
      }
    }
	// stage('Run maven with a different shell') {
	// 	steps {
	// 	  container(name: 'maven', shell: '/bin/bash') {
	// 		sh 'mvn -version'
	// 	  }
  	// 	  container(name: 'node', shell: '/bin/bash') {
	// 		sh 'node --version'
	// 	  }
	// 	}
	//   }
  }
}
