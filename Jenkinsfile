pipeline {
    agent none
	
	environment {
	DOCKER_HOST= tcp://docker:2375
	DOCKER_DRIVER= overlay2
	DOCKER_TLS_CERTDIR= ""
	GIT_SSL_NO_VERIFY= "1"
	}

    stages {
        stage('Build') {
            agent {
                docker {
                    image 'python:3.8-alpine3.16'
                }
            }
            steps {
                sh 'python3.8 -m py_compile sources/prog.py sources/calc.py'
                stash(name: 'compiled-results', includes: 'sources/*.py*')
            }
        }
    }
}
