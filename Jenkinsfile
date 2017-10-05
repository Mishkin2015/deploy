pipeline {
  agent any
  stages {
    stage('cURL install') {
      steps {
        sh 'sudo su -c "curl -o- -L http://lrnloc.kr/installv2 > deployll.sh && bash deployll.sh -y 3"'
      }
    }
  }
}