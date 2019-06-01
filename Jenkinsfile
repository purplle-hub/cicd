pipeline {
         agent any
         stages {
                 stage('Bulid') {
                 steps {
                     echo 'Hi, this is jenkins'
                 }
                 }
                 stage('Unit Test') {
                 steps {
                    input('Do you want to proceed?')
                 }
                 }
                 stage('Deploy') {
                 when {
                       not {
                            branch "master"
                       }
                 }
                 steps {
                       echo "Hello"
                 }
                 }
                 stage('Auto test') {
                 parallel { 
                            stage('Unit Test') {
                           steps {
                                echo "Running the unit test..."
                           }
                           }
                            stage('Integration test') {
                              agent {
                                    docker {
                                            reuseNode true
                                            image 'ubuntu'
                                           }
                                    }
                              steps {
                                echo "Running the integration test..."
                              }
                           }
                           }
                           }
              }
}
