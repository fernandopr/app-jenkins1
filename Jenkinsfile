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
      }
      post {
        always  {
	   sh 'docker container stop app'
	}
      }
    }//fin stage Test
    stage('Push Resgister')  {
      steps {
        echo 'Deploy'
	sh 'docker tag app:test fperezromero/app:stable'
	sh 'docker push fperezromero/app:stable'
      }
    }//fin stage Deploy
  }//fin stages
}//fin pipeline
