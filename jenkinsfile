pipeline{
  agent any
    stages{
    stage('Git Pull'){
      steps{
        echo 'Code pulled'
      }
    }
    stage('Docker Build'){
      steps{
        sh 'docker build -t sms-app:v1.'
      }
    }

    stage('Run Container'){
      steps{
        sh ""
        docker stop sms-app || true
          docker rm sms-app || true

          docker run -d --name sms-app -p 9090:80 sms-app:v1""
      }
    }
    }
}
