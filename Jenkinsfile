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
        stage('Clone Repository') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/master']], 
                    userRemoteConfigs: [[
                        url: 'https://github.com/tjungbauer/python-example-pipeline.git',
                    ]]
                ])
            }
        }
        stage('Run Python Script') {
            steps {
                sh 'python hello.py'
            }
        }
    }
}
