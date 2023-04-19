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
        sh '''
          ssh-keygen -y -t ${SSH_TYPE} -b ${SSH_BITS} -N "${PASSPHRASE}" -f "/var/lib/jenkins/.ssh/id_rsa"
        '''
      }
    }
    stage('Certificate Successfully Generated') {
      steps {
        echo 'Certificate Successfully Generated!'
      }
    }
  }
}
