pipeline {
	agent any
	tools {
		maven 'maven 3.9.9'
	}

	parameters {
		choice(name: 'DEPLOY_ENVIRONMENT', choices: ['ninguno', 'tomee'], description: 'Ambiente de despliegue')
	}

	stages {
		stage('PackageDocker') {
			steps {
				bat 'mvn -B -q clean package'
			}
		}
		stage('Deploy') {
			when {
				not {
					equals expected: 'ninguno', actual: params.DEPLOY_ENVIRONMENT
				}
			}
			steps {
				bat 'copy target\\ear-example-0.0.1.ear C:\\Users\\virtual\\ambientes\\apache-tomee-plus-10.0.0-M3\\apps\\'
			}
		}
	}
}
