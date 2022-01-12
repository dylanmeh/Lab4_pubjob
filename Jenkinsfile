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
                publishEvent jsonEvent('{"labs":[{"lab":"1"},{"lab":"2"},{"lab":"3"},{"lab":"4"},{"lab":"5"},{"lab":"6"},{"lab":"7"}],"unitTestEnable":"true"}')
            }
        }
    }
}