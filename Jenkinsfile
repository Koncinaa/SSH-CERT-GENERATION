pipeline {
  agent any
  
  stages {
    stage('Checkout from Git') {
      steps {
        checkout([
          $class: 'GitSCM',
          branches: [[name: '*/master']],
          userRemoteConfigs: [[url: '${Github}']]
        ])
      }
    }
    
    stage('Generate New Certificate') {
      steps {
        sh 'ssh-keygen -t rsa -b 4096 -N "" -f id_rsa'
      }
    }
    stage('Certificate Successfully Generated') {
      steps {
        echo 'Certificate Successfully Generated!'
      }
    }
  }
}
