pipeline {
  agent any
  stages {
    stage('Git Pull') {
      steps {
        echo 'Code pulled'
      }
    }
    stage('SonarQube Scan') {
      steps {
        sh '''
          docker run --rm \
            --network host \
            --volumes-from jenkins \
            -w /var/jenkins_home/workspace/sms-cicd \
            sonarsource/sonar-scanner-cli \
            -Dsonar.host.url=http://localhost:9000 \
            -Dsonar.login=squ_fdb58901ea8a7dd09b80b758b0911613d77ad63a
        '''
      }
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
