pipeline {
    agent {
        kubernetes {
            yaml '''
        apiVersion: v1
        kind: Pod
        spec:
          containers:
          - name: node
            image: node:16.13.1-alpine
            command:
            - cat
            tty: true
          - name: git
            image: alpine/git
            command:
            - sleep
            args:
            - infinity
          - name: fastlane
            image: softartdev/android-fastlane
            command:
            - sleep
            args:
            - infinity
            '''
        }
    }
    stages {
            stage('prep') {
                steps {
                git url: 'https://github.com/Shfarrukhb/android-project.git', branch: 'main'
                }
            }
            stage('fastlane') {
                steps{
                    container('fastlane') {
                        sh 'ls /home/jenkins/agent/workspace/'
                        //sh 'cat pwd.txt'
                        
                        
                     //   sh 'fastlane dev'
                      //  sh 'fatlane prod'
                       }
                    }
                }
            
    }
}
