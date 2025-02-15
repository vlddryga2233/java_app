pipeline {
    agent {
        kubernetes {
            yaml '''
            apiVersion: v1
            kind: Pod
            spec:
              containers:
              - name: maven
                image: vlad1020/java-21-builder
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