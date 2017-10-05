pipeline {
  agent any
  stages {
    stage('Run deploy script') {
      steps {
        sh 'sudo su -c "bash ./llv2_build.sh -y 3"'
      }
    }
    stage('Test Processes') {
      steps {
        parallel(
          "Test xAPI": {
            sh 'bash ./tests/checkURL.sh -u localhost/data/xAPI/about'
          },
          "Test API": {
            sh 'bash ./tests/checkURL.sh -u localhost/api'
          },
          "Test UI": {
            sh 'bash ./tests/checkURL.sh -u localhost'
          }
        )
      }
    }
    stage('Print Logs') {
      steps {
        sh 'cat /var/log/learninglocker/install.log'
        sh 'cat /var/log/learninglocker/xapi_stdout*.log'
        sh 'cat /var/log/learninglocker/api_stdout*.log'
        sh 'cat /var/log/learninglocker/ui_stdout*.log'
        sh 'cat /var/log/learninglocker/worker_stdout*.log'
        sh 'cat /var/log/learninglocker/xapi_stderr*.log'
        sh 'cat /var/log/learninglocker/api_stderr*.log'
        sh 'cat /var/log/learninglocker/ui_stderr*.log'
        sh 'cat /var/log/learninglocker/worker_stderr*.log'
      }
    }
  }
}
