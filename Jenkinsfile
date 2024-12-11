pipeline {
    agent {
        kubernetes {
            yaml '''
                apiVersion: v1
                kind: Pod
                spec:
                  containers:
                    - name: python
                      image: python:3.9-slim
                      command:
                        - sleep
                      args:
                        - infinity
                 '''
            defaultContainer 'python'
        }
    }
    stages {
        stage('Run Python Script') {
            steps {
                sh 'python hello.py'
            }
        }
    }
}
