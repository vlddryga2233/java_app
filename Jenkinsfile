pipeline {
    agent {
        kubernetes {
            yaml '''
            apiVersion: v1
            kind: Pod
            spec:
              containers:
              - name: maven
                image: maven:alpine
                command:
                - cat
                tty: true
            '''
        }
    }

    stages {
        stage('Maven version'){
            steps {
                sh 'mvn --verison'
            }
        }
    }
}