pipeline {
  agent any
  
  stages {
    stage('Checkout from Git') {
      steps {
        checkout([
          $class: 'GitSCM',
          branches: [[name: '*/master']],
          userRemoteConfigs: [[url: 'https://github.com/Koncinaa/SSH-CERT-GENERATION.git']]
        ])
      }
    }
    
    stage('Generate New Certificate') {
      steps {
        sh 'ssh-keygen -t rsa -b 4096 -N "" -f "/var/lib/jenkins/.ssh/${SSH_NAME}"'
      }
    }
    stage('Certificate Successfully Generated') {
      steps {
        echo 'Certificate Successfully Generated!'
      }
    }
  }
}
