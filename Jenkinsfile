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
      }
    }//fin stage Test
    stage('Push Resgister')  {
      steps {
        echo 'Deploy'
      }
    }//fin stage Deploy
  }//fin stages
}//fin pipeline
