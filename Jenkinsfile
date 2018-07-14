pipeline  {
  agent any
  stages  {
    stage('Build')  {
      steps {
        sh 'docker build -t app .'
      }
    } //fin stage Build
    stage('Test') {
      steps {
        echo 'Test'
	sh '/bin/nc -vz localhost 8080'
	sh '/bin/nc -vz localhost 80'
	sh '/bin/nc -vz localhost 22'
      }
    }//fin stage Test
    stage('Push Resgister')  {
      steps {
        echo 'Deploy'
	sh 'docker tag app:test app:stable'
	sh 'docker push fernandopr/app:stable'
      }
    }//fin stage Deploy
  }//fin stages
}//fin pipeline
