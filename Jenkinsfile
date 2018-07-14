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
      }
    }//fin stage Test
    stage('Deploy')  {
      steps {
        echo 'Deploy'
      }
    }//fin stage Deploy
  }//fin stages
}//fin pipeline
