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
        stage('Validate maven version'){
            steps {
                container('maven'){
                    sh 'mvn --version'
                }
            }
        }
        stage('Build Java Application'){
            steps {
                container('maven'){
                    sh 'mvn clean install'
                    sh 'ls -la'
                }
            }
        }
    }
}