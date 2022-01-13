pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: build
    image: 'maven:3.8.3-jdk-11'
    command:
    - cat
    tty: true
    '''
        defaultContainer 'build'
        }
    }

    stages {
        stage('Sending notification') {
            steps {
                echo 'sending json data for unit testing in downstream job'
                publishEvent jsonEvent('{"labs":[{"lab1":"1"},{"lab2":"2"},{"lab3":"3"},{"lab4":"4"},{"lab5":"5"},{"lab6":"6"},{"lab7":"7"}],"unitTestEnable":"true"}')

            }
        }
    }
}