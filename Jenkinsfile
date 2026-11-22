pipeline {
  agent any
  stages {
    stage('Git Pull') {
      steps {
        echo 'Code pulled'
      }
    }
    stage('Docker Build') {
      steps {
        sh 'docker build -t sms-app:v1 .'
      }
    }
    stage('Run Container') {
      steps {
        sh 'docker rm -f sms-app || true'
        sh 'docker run -d --name sms-app -p 9091:80 sms-app:v1'
      }
    }
  }
}
