pipeline {
  agent {
    kubernetes {
      yaml '''
        apiVersion: v1
        kind: Pod
        metadata:
          labels:
            ruby: 3.3
        spec:
          containers:
          - name: ruby
            image: ruby:3.3
            command:
            - sleep
            args:
            - 99d
            tty: true
        '''
      retries 2
    }
  }
  stages {
    stage('Run ruby') {
      steps {
        container('ruby') {
          sh 'ls -l'
          sh 'pwd'
          sh 'ls -l /home/jenkins/agent'
          sh 'ruby --version'
          sh 'ruby ./helloworld.rb'
        }
      }
    }
  }
}
