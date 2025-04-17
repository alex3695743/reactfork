pipeline {
    agent {
        docker {
            image 'node:20.10.0-alpine3.18'
            args '-p 3000:3000'
        }
    }

    stages {
        stage('Build') {
            steps {
                // Limpieza preventiva para evitar el ENOTEMPTY
                sh 'rm -rf node_modules package-lock.json'
                sh 'npm install'
            }
        }
	stage('Test') {
	    steps {
		sh 'chmod +x ./jenkins/scripts/test.sh'
		sh './jenkins/scripts/test.sh'
	    }
        }
    }
}
