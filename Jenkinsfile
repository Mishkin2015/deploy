pipeline {
  agent any
  stages {
    stage('Run deploy script') {
      steps {
        sh 'sudo su -c "bash llv2_build.sh -y 3"'
      }
    }
  }
}