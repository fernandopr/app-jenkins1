pipeline  {
  agent any
  stages  {
    stage('Build')  {
      steps {
        sh 'docker build -t app:test .'
      }
    } //fin stage Build
    stage('Test') {
      steps {
        echo 'Test'
        sh 'docker run --rm --name app -id -p 80:80 app:test'
        sh '/bin/nc -vz localhost 80'
        sh 'docker stop app'
      }
    }//fin stage Test
    stage('Push Resgister')  {
      steps {
        withCredentials([usernamePassword(credentialsId: '0fcf4b93-7ed4-4e9b-ae8b-7f7d0f72060e', passwordVariable: 'passwd', usernameVariable: 'user')]) {
          sh 'docker tag app:test fperezromero/app:stable'
          sh 'docker push fperezromero/app:stable'
        }
      }
    }//fin stage Push register
  }//fin stages
}//fin pipeline
