pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'javac TestHelloWorld.java' 
                fingerprint: true
            }
        }
        stage('Test') {
	    steps {
                /* `make check` returns non-zero on test failures,
                * using `true` to allow the Pipeline to continue nonetheless
                */
                sh 'javac AllTests.java' 

            }
        }
        stage('Deploy') {
            when {
              expression {
                currentBuild.result == null || currentBuild.result == 'SUCCESS' 
              }
            }
            steps {
                sh 'javac HelloWorld.java'
            }
        }
    }
}
