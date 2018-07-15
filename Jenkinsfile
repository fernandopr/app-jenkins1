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
        sh 'docker tag app:test fperezromero/app:stable'
        withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials', passwordVariable: 'pass', usernameVariable: 'user')]) {
          sh 'docker login -u ${user} -p ${pass}'
        }
          sh 'docker push fperezromero/app:stable'
        }
      }
    }//fin stage Push register
  }//fin stages
}//fin pipeline
