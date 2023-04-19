pipeline {
  agent any
  
  stages {
    stage('Setup parameters') {
            steps {
                script { 
                    properties([
                        parameters([
                            choice(
                                choices: ['rsa'], 
                                name: 'SSH_TYPE'
                            ),
                            choice(
                                choices: ['2048'],
                                name: 'SSH_BITS'
                            ),
                            string(
                                defaultValue: '', 
                                name: 'PASSPHRASE', 
                                trim: true
                            },
                            string(
                                defaultValue: '', 
                                name: 'SSH_NAME', 
                                trim: true
                            )
                        ])
                    ])
                }
            }
        }
    
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
        sh 'ssh-keygen -t ${SSH_TYPE} -b ${SSH_BITS} -N "${PASSPHRASE}" -f "/var/lib/jenkins/.ssh/${SSH_NAME}"'
      }
    }
    
    stage('Certificate Successfully Generated') {
      steps {
        echo 'Certificate Successfully Generated!'
      }
    }
  }
}
